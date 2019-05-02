---
title: Configuración de Exchange Connector local de Microsoft Intune
titleSuffix: Microsoft Intune
description: Use Exchange Connector local para administrar el acceso del dispositivo a los buzones de Exchange en función de la inscripción de Intune y Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3724f2494dd4e4fe7939a9be87a30e1bc5bfbf27
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513603"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>Configuración de Exchange Connector local de Intune en Microsoft Intune
La información de este artículo le ayudará a instalar y, luego, supervisar el conector local de EAS de Intune.  Exchange Connector local de Intune se usa con las [directivas de acceso condicional para permitir o bloquear el acceso a los buzones locales de Exchange](conditional-access-exchange-create.md). 

Cuando un dispositivo intenta acceder a Exchange en el entorno local, Exchange Connector asigna registros de Exchange Active Sync (EAS) en Exchange Server a los registros de Intune con el fin de comprobar la inscripción de los dispositivos en Intune y el cumplimiento de las directivas de dispositivo correspondientes. En función de las directivas de acceso condicional, el dispositivo puede tener acceso o estar bloqueado. Consulte [¿Cuáles son las formas habituales de usar el acceso condicional con Intune?](conditional-access-intune-common-ways-use.md) para obtener más información.

Intune admite la instalación de varios conectores Exchange locales por suscripción. Si tiene más de una organización de Exchange local, puede configurar un conector independiente para cada una de ellas. Sin embargo, solo se puede instalar un conector para su uso en cada organización de Exchange. 

Para configurar una conexión que permita a Intune comunicarse con una instancia local de Exchange Server, debe seguir los pasos siguientes:

1. Descargue Exchange Connector local de Intune del portal de Intune.
2. Instale y configure Exchange Connector en un equipo de la organización de Exchange local.
3. Valide la conexión de Exchange.
4. Repita estos pasos para cada organización adicional de Exchange que quiera conectar a Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Requisitos de la instancia local de Intune Exchange Connector
Necesitará una cuenta con una licencia de Intune que pueda usar el conector para conectarse a Exchange. La cuenta se especifica al instalar el conector.  

En esta tabla se indican los requisitos del equipo en el que se instala la instancia local de Exchange Connector.  

|  Requisito  |   Más información     |
|---------------|------------------------|
|  Sistemas operativos        | Intune admite la instancia local de Exchange Connector en equipos con Windows Server 2008 SP2 de 64 bits, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 o Windows Server 2016.<br /><br />El conector no es compatible con ninguna instalación de Server Core.  |
| Microsoft Exchange          | Para la instancia local de Exchange Connector se necesita Microsoft Exchange 2010 SP3 o una versión posterior o Exchange Online dedicado heredado. Para determinar si la configuración de su entorno Exchange Online dedicado es <strong>nueva</strong> o <strong>heredada</strong>, póngase en contacto con su administrador de cuentas. |
| Entidad de administración de dispositivos móviles           | [Establecer la entidad de administración de dispositivos móviles en Intune](mdm-authority-set.md). |
| Hardware              | El equipo donde se instala el conector debe requiere una CPU de 1,6 GHz con 2 GB de RAM y 10 GB de espacio libre en disco. |
|  Sincronización de Active Directory             | Para poder usar el conector para conectar Intune a su instancia de Exchange Server, debe [configurar la sincronización de Active Directory](users-add.md) de forma que los usuarios locales y los grupos de seguridad estén sincronizados con su instancia de Azure Active Directory. |
| Software adicional         | El equipo que hospede el conector debe tener una instalación completa de Microsoft .NET Framework 4.5 y Windows PowerShell 2.0. |
| Network (Red)               | El equipo en el que se instala el conector debe estar en un dominio que tenga una relación de confianza con el dominio que hospeda Exchange Server.<br /><br />El equipo requiere configuraciones que le permitan obtener acceso al servicio de Intune a través de firewalls y servidores proxy mediante los puertos 80 y 443. Entre los dominios usados por Intune están manage.microsoft.com, &#42;manage.microsoft.com y &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Requisitos del cmdlet de Exchange

Cree una cuenta de usuario de Active Directory que se usará en la instancia local de Exchange Connector. La cuenta debe tener permiso para ejecutar los siguientes cmdlets de Windows PowerShell Exchange necesarios:


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Descarga del paquete de instalación de software de la instancia local de Exchange Connector

1. En un sistema operativo Windows Server compatible con la instancia local de Exchange Connector, abra [Azure Portal](https://portal.azure.com) e inicie sesión con una cuenta de usuario que sea administrador de la instancia local de Exchange Server y que disponga de una licencia para usar Exchange Server.

2. Vaya a **Intune** > **Acceso de Exchange**.  

3. En **Configuración**, elija **Exchange ActiveSync Connector local** y, luego, seleccione **Agregar**.

4. En la página **Agregar conector**, seleccione **Descargar el conector local**. El conector local de Exchange se encuentra en una carpeta comprimida (.zip) que se puede abrir o guardar. En el cuadro de diálogo **Descarga de archivos**, haga clic en **Guardar** para almacenar la carpeta comprimida en una ubicación segura.

    > [!IMPORTANT]
    > No cambie el nombre ni mueva los archivos de la carpeta de la instancia local de Exchange Connector. Si lo hace, se producirá un error en la instalación de Exchange Connector.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Instalar y configurar Intune On-Premises Exchange Connector
Siga estos pasos para instalar Intune On-Premises Exchange Connector. Si tiene varias organizaciones de Exchange, repita estos pasos para cada conector de Exchange adicional que quiera instalar.

1. En un sistema operativo compatible con On-Premises Exchange Connector, extraiga los archivos de **Exchange_Connector_Setup.zip** en una ubicación segura.

2. Una vez extraídos los archivos, abra la carpeta extraída y haga doble clic en **Exchange_Connector_Setup.exe** para instalar On-Premises Exchange Connector.

   > [!IMPORTANT]
   > Si la carpeta de destino no es una ubicación segura, debe eliminar el archivo de certificado **MicrosoftIntune.accountcert** cuando termine de instalar On-Premises Exchange Connector.

3. En el cuadro de diálogo de **Microsoft Intune Exchange Connector**, seleccione **Microsoft Exchange Server local** o **Microsoft Exchange Server hospedado**.

   ![Imagen que muestra dónde debe elegir el tipo de Exchange Server](./media/intune-sa-exchange-connector-config.png)

   Para un servidor Exchange local, proporcione el nombre del servidor o el nombre de dominio completo del servidor Exchange que hospeda el rol de **servidor de acceso de cliente**.

   Para un servidor de Exchange hospedado, proporcione la dirección del servidor Exchange. Para buscar la dirección URL del servidor Exchange hospedado:

   1. Abra Outlook en la web para Office 365.

   2. Elija el icono **?** de la esquina superior izquierda y luego seleccione **Acerca de**.

   3. Busque el valor **Servidor externo POP** .

   4. Elija **Servidor proxy** para especificar la configuración del servidor proxy para el servidor Exchange hospedado.
       1. Seleccione **Usar un servidor proxy al sincronizar información de dispositivos móviles**.

       2. Escriba el **nombre del servidor proxy** y el **número de puerto** que se utilizará para tener acceso al servidor.

       3. Si es necesario proporcionar credenciales de usuario para acceder al servidor proxy, seleccione **Usar credenciales para conectarse al servidor proxy**. A continuación, escriba el **dominio\usuario** y la **contraseña**.

       4. Elija **Aceptar**.

4. En los campos **Usuario (Dominio\usuario)** y **Contraseña**, escriba las credenciales que son necesarias para conectarse a su servidor de Exchange. La cuenta que se especifique debe tener una licencia para usar Intune. 

5. Proporcione las credenciales necesarias para enviar notificaciones al buzón de Exchange Server de un usuario. Este usuario se puede destinar solo a las notificaciones. El usuario de notificaciones necesita un buzón de Exchange para enviar notificaciones por correo electrónico. Puede configurar estas notificaciones con directivas de acceso condicional en Intune.  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. En el campo **Contraseña**, indique la contraseña de la cuenta para permitir que Intune obtenga acceso al servidor Exchange.

7. Elija **Conectar**.

   > [!NOTE]
   > La conexión puede tardar unos minutos en configurarse.

Durante la configuración, Exchange Connector guarda la configuración de proxy para permitir el acceso a Internet. Si cambia la configuración de proxy, tiene que volver a configurar el conector de Exchange para aplicarle la configuración de proxy actualizada.

Después de que Exchange Connector configure la conexión, los dispositivos móviles asociados a los usuarios administrados en Exchange se sincronizan automáticamente y se agregan a Exchange Connector. Esta sincronización puede tardar algún tiempo en completarse.

> [!NOTE]
> Si ha instalado On-Premises Exchange Connector y en algún momento elimina la conexión de Exchange, deberá desinstalar On-Premises Exchange Connector del equipo en el que se instaló.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Instalar conectores para varias organizaciones de Exchange
Intune admite varias instancias de On-premises Exchange Connector por suscripción. Para un inquilino con varias organizaciones de Exchange, se puede configurar un conector para cada organización de Exchange, pero solo un único conector para cada organización única. 

Si va a instalar conectores para conectarse a varias organizaciones de Exchange, descargue la carpeta .zip una vez y, después, vuelva a usar esa misma descarga para cada conector que instale. Para cada conector adicional, siga los pasos descritos en la sección anterior para extraer y ejecutar el programa de instalación en un servidor en la organización de Exchange.

Las características de alta disponibilidad, supervisión y sincronización manual que se describen en las secciones siguientes se admiten para cada organización de Exchange que se conecta a Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Compatibilidad de alta disponibilidad de On-premises Exchange Connector 
El término "alta disponibilidad" para Exchange Connector local indica que el servidor de acceso de cliente (CAS) de Exchange que usa el conector debería permanecer deshabilitado; el conector puede cambiar con el fin de usar un CAS diferente para esa organización de Exchange. El propio Exchange Connector no es compatible con la alta disponibilidad. Si se produce un error en el conector, no hay ninguna conmutación automática por error y se debe reemplazar dicho conector [instalando otro](#reinstall-the-on-premises-exchange-connector). 

Para realizar la conmutación por error, después de que el conector establezca una conexión correcta con Exchange mediante el CAS especificado, este detectará CAS adicionales para esa organización de Exchange. El conocimiento de CAS adicionales permite al conector conmutar por error en otro CAS (si hay alguno disponible) hasta que el CAS principal esté disponible. De forma predeterminada, está habilitada la detección de CAS adicionales. Puede desactivar la conmutación por error mediante el procedimiento siguiente:  
1. En el servidor en el que esté instalado Exchange Connector, vaya a %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Con un editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Cambie &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; a &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; para deshabilitar la característica.    
 

## <a name="reinstall-the-on-premises-exchange-connector"></a>Reinstalación de Exchange Connector local
Es posible que deba reinstalar un conector de Exchange. Dado que solo se admite un conector para conectarse a cada organización de Exchange, si se instala un segundo conector para una organización, el nuevo que se instale reemplazará el original.

1. Siga los pasos disponibles en [Instalar y configurar Intune On-Premises Exchange Connector](#install-and-configure-the-intune-on-premises-exchange-connector) para iniciar la instalación del nuevo conector. 
2. Cuando se le solicite, seleccione **Reemplazar** para instalar el nuevo conector.  
   ![Petición de configuración para reemplazar un conector](./media/exchange-connector-install/prompt-to-replace.png)

3. Continúe con los pasos descritos en el procedimiento anterior y vuelva a iniciar sesión en Intune.
4. Cuando llegue a la pantalla final, seleccione **Cerrar** para completar la instalación.  
   ![Instalación completada](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Supervisión de la actividad de Exchange Connector

Después de haber configurado correctamente el conector de Exchange, puede ver el estado de las conexiones y la última sincronización correcta. Para validar la conexión del conector de Exchange:

1. En el panel de Intune, elija **Acceso de Exchange**.
2. Seleccione **Acceso local a Exchange** para verificar el estado de la conexión para cada conector de Exchange.

También puede comprobar la fecha y la hora del último intento de sincronización correcto.
--> 

### <a name="system-center-operations-manager-management-pack"></a>Módulo de administración de System Center Operations Manager

A partir de la versión 1710 de Intune, puede usar el [módulo de administración de Operations Manager para el conector de Exchange e Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Con el uso del módulo de administración se proporcionan distintas maneras de supervisar el conector de Exchange cuando haya que resolver problemas.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forzar manualmente una sincronización rápida o una sincronización completa
Un conector de Exchange local sincroniza automáticamente registros de dispositivos de EAS e Intune regularmente. Si cambia el estado de cumplimiento de un dispositivo, el proceso de sincronización automática actualiza regularmente los registros para que el acceso a los dispositivos pueda bloquearse o permitirse.

   - La **Sincronización rápida** se produce con regularidad, varias veces al día. Una sincronización rápida recupera información del dispositivo para usuarios con licencia de Intune y con destino de acceso condicional a On-premises Exchange que hayan cambiado desde la última sincronización.

   - La **Sincronización completa** se realiza una vez al día de manera predeterminada. Una sincronización completa recupera información del dispositivo para todos los usuarios con licencia de Intune y con destino de acceso condicional a On-premises Exchange. Una sincronización completa también recupera información de Exchange Server y se asegura de que la configuración especificada por Intune en Microsoft Azure Portal se actualiza en Exchange Server. 


Puede forzar que un conector ejecute una sincronización mediante las opciones **Sincronización rápida** o **Sincronización completa** en el panel de Intune con los pasos siguientes:

   1. En el panel de Intune, elija **Acceso de Exchange**.
   2. Seleccione **Acceso local a Exchange**.
   3. Seleccione el conector que quiere sincronizar y elija **Sincronización rápida** o **Sincronización completa**.

## <a name="next-steps"></a>Pasos siguientes
[Creación de una directiva de acceso condicional para el entorno local de Exchange](conditional-access-exchange-create.md)
