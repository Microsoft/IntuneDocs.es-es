---
title: Administración del acceso web corporativo con un explorador protegido por directiva
titleSuffix: Microsoft Intune
description: Use un explorador protegido por directiva asignado por Intune para administrar la transferencia de datos web y la exploración web de una empresa.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f32cfbb5e05958ec9d8f303809d3ffa28c3a3ec
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569732"
---
# <a name="manage-web-access-using-a-microsoft-intune-policy-protected-browser"></a>Administración del acceso web con un explorador protegido por directiva de Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mediante un explorador protegido por una directiva de Intune (Microsoft Edge o Intune Managed Browser), tendrá la garantía de que el acceso a los sitios web corporativos se hace siempre con las medidas de seguridad adecuadas.  Cuando se configuran con Intune, los exploradores protegidos presentan estas ventajas:

- Directivas de protección de aplicaciones
- Acceso condicional
- Inicio de sesión único
- Parámetros de configuración de la aplicación
- Integración de proxy de la aplicación de Azure

## <a name="microsoft-edge-support"></a>Compatibilidad de Microsoft Edge

Puede usar Microsoft Edge para escenarios empresariales en dispositivos iOS y Android. Microsoft Edge admite los mismos escenarios de administración que Intune Managed Browser con la incorporación de mejoras en la experiencia del usuario final. Están disponibles las características empresariales de Microsoft Edge siguientes habilitadas por directivas de Intune. Estas características empresariales incluyen:

1. **Identidad dual**: los usuarios pueden agregar una cuenta profesional, al igual que una cuenta personal, para realizar la exploración. Hay una separación total entre ambas identidades, que es similar a la arquitectura y experiencia existente en Office 365 y Outlook. Los administradores de Intune podrán establecer las directivas deseadas para lograr una experiencia de exploración protegida dentro de la cuenta profesional. 
2. **Integración de directivas de protección de la aplicación Intune**: los administradores ahora pueden dirigir las directivas de protección de aplicación a Microsoft Edge, incluido el control de las acciones de cortar, copiar y pegar, lo que impide las capturas de pantalla y garantiza que los vínculos seleccionados por el usuario solo se abran en otras aplicaciones administradas.
3. **Integración de proxy de la aplicación de Azure**: los administradores pueden controlar el acceso a las aplicaciones web y a las aplicaciones SaaS, lo que permite garantizar que las aplicaciones basadas en explorador solo se ejecuten en el explorador seguro de Microsoft Edge, ya sea que los usuarios finales se conecten desde la red corporativa o desde Internet. 
4. **Favoritos administrados y accesos directos a la página principal**: para facilitar el acceso, los administradores pueden establecer direcciones URL para que aparezcan en los favoritos cuando los usuarios finales estén en su contexto corporativo. Los administradores pueden establecer un acceso directo a la página principal, que se mostrará como el acceso directo principal cuando el usuario corporativo abra una página o una pestaña nueva en Microsoft Edge.

Las directivas de protección de Microsoft Intune para Microsoft Edge ayudan a proteger los datos y los recursos de su organización. Microsoft Edge protegido por Intune garantiza que los recursos de su empresa están protegidos no solo dentro de las aplicaciones instaladas de manera nativa, sino también cuando se acceden a través del explorador web.

## <a name="getting-started"></a>Introducción

Microsoft Edge e Intune Managed Browser son aplicaciones de explorador web que usted y sus usuarios finales pueden descargar desde las tiendas de aplicaciones públicas para usarlas en la organización. 

Requisitos del sistema operativo para las directivas de explorador:
- Android 4 y versiones posteriores
- iOS 8.0 y versiones posteriores.

Las versiones anteriores de iOS y Android podrán seguir usando Intune Managed Browser, pero no podrán instalar nuevas versiones de la aplicación y es posible que no puedan tener acceso a todas las funcionalidades de la aplicación. Le recomendamos que actualice la versión del sistema operativo de estos dispositivos a una que sea compatible.

>[!NOTE]
>Managed Browser no es compatible con el protocolo de cifrado de Capa de sockets seguros versión 3 (SSLv3).


## <a name="application-protection-policies-for-protected-browsers"></a>Directivas de protección de aplicaciones para exploradores protegidos

Como Microsoft Edge y Managed Browser disponen de integración con el SDK de Intune, también puede aplicarles directivas de protección de aplicaciones, lo que incluye:
- Controlar el uso de cortar, copiar y pegar
- Evitar las capturas de pantalla
- Garantizar que los vínculos corporativas se abren solo en aplicaciones y exploradores administrados

Para obtener detalles, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

Puede aplicar esta configuración a:

- Dispositivos móviles inscritos con Intune
- Inscritos con otro producto de MDM
- Dispositivos no administrados

>[!NOTE]
>Si los usuarios instalan Managed Browser desde la tienda de aplicaciones y no lo administra Intune, se puede utilizar como un explorador web básico, con compatibilidad para el inicio de sesión único a través del sitio de Microsoft MyApps. A los usuarios se les remite directamente al sitio de MyApps, donde pueden ver todas las aplicaciones SaaS aprovisionadas.
Dado que Intune no administra Managed Browser ni Microsoft Edge, no pueden acceder a los datos de otras aplicaciones administradas por Intune. 


## <a name="conditional-access-for-protected-browsers"></a>Acceso condicional para exploradores protegidos

Ahora, Managed Browser es una aplicación de cliente aprobada para el acceso condicional. Esto significa que se puede restringir el acceso de explorador móvil a únicamente las aplicaciones web conectadas a Azure AD donde solo se puede usar Managed Browser, e impedir el acceso desde cualquier otro explorador no protegido, como Safari o Chrome. Esta protección se puede aplicar a recursos de Azure como Exchange Online y SharePoint Online, el Centro de administración de Microsoft 365 e, incluso, a sitios locales que estén expuestos a usuarios externos a través del [proxy de la aplicación de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). 

Para limitar las aplicaciones web conectadas a Azure AD al uso de Intune Managed Browser en plataformas móviles, puede crear una directiva de acceso condicional que requiera aplicaciones de cliente aprobadas. 

> [!TIP]  
> Acceso condicional es una tecnología de Azure Active Directory (Azure AD). El nodo de acceso condicional al que se accede desde *Intune* es el mismo nodo al que se accede desde *Azure AD*.  


1. En el portal de Intune, seleccione **Acceso condicional** > **Nueva directiva**. 
2. Luego, seleccione **Conceder** en la sección **Controles de acceso** de la hoja. 
3. Haga clic en **Requerir aplicación cliente aprobada**. 
4. Haga clic en **Seleccionar** en la hoja **Conceder**. Esta directiva se debe asignar a las aplicaciones en la nube que quiera que estén accesibles a únicamente la aplicación Intune Managed Browser.

    ![Azure AD - Directiva de acceso condicional de Managed Browser](./media/managed-browser-conditional-access-01.png)

5. En la sección **Asignaciones**, seleccione **Condiciones** > **Aplicaciones cliente**. Aparece la hoja **Aplicaciones cliente**.
6. Haga clic en **Sí** en **Configurar** para aplicar la directiva a aplicaciones cliente específicas.
7. Compruebe que **Explorador** está seleccionado como aplicación cliente.

    ![Azure AD - Managed Browser - Selección de aplicaciones cliente](./media/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Si quiere restringir qué aplicaciones nativas (aplicaciones que no son de explorador) pueden tener acceso a estas aplicaciones en la nube, también puede seleccionar **Aplicaciones móviles y aplicaciones de escritorio**.

8. En la sección **Asignaciones**, seleccione **Usuarios y grupos** y, después, elija los usuarios o grupos a los que quiera asignar esta directiva. 

    > [!NOTE]
    > A los usuarios también se les deben asignar directivas de Intune App Protection para recibir directivas de configuración de aplicaciones. Para obtener más información sobre cómo crear directivas de Intune App Protection, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

9. En la sección **Asignaciones**, seleccione **Aplicaciones en la nube** para elegir las aplicaciones que se van a proteger con esta directiva.

Una vez configurada la directiva, los usuarios deberán usar inexorablemente Intune Managed Browser para tener acceso a las aplicaciones web conectadas a Azure AD que estén protegidas con dicha directiva. Si los usuarios intentan usar un explorador no administrado en este escenario, aparecerá un aviso que les indica que deben usar Intune Managed Browser en su lugar.

Managed Browser no admite directivas de acceso condicional clásicas. Para obtener más información, vea [Migración de directivas clásicas en Azure Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration).

##  <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Inicio de sesión único en aplicaciones web conectadas a Azure AD en exploradores protegidos por directivas

Microsoft Edge e Intune Managed Browser en iOS y Android pueden aprovechar el inicio de sesión único en todas las aplicaciones web (SaaS y locales) que estén conectadas a Azure AD. Si la aplicación Microsoft Authenticator está presente en iOS o la aplicación Portal de empresa de Intune lo está en Android, los usuarios de un explorador protegido por directivas podrán acceder a aplicaciones web conectadas a Azure AD sin tener que volver a escribir sus credenciales.

Para el inicio de sesión único hace falta que el dispositivo esté registrado con la aplicación Microsoft Authenticator en iOS o con el Portal de empresa de Intune en Android. Los usuarios que tengan las aplicaciones Authenticator o Portal de empresa de Intune deberán registrar su dispositivo cuando vayan a una aplicación web conectada a Azure AD en un explorador protegido por directivas, si el dispositivo aún no se ha registrado por medio de otra aplicación. Una vez que el dispositivo esté registrado con la cuenta administrada por Intune, esa cuenta tendrá habilitado el inicio de sesión único en las aplicaciones web conectadas a Azure AD. 

> [!NOTE]
> El registro de dispositivos consiste en un sencillo registro en el servicio de Azure AD. No se requiere una inscripción de dispositivo completa ni se otorga a TI ningún tipo de privilegio extra en el dispositivo.

## <a name="create-a-protected-browser-app-configuration"></a>Establecimiento de una configuración de aplicaciones de explorador protegido

>[!IMPORTANT]
>Para que se apliquen las configuraciones de aplicaciones, el explorador protegido del usuario u otra aplicación del dispositivo ya deben estar administrados mediante [directivas de aplicación de Intune]( app-protection-policy.md)

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3.  En la hoja **Aplicaciones cliente** de la lista Administrar, elija **Directivas de configuración de aplicaciones**.
4.  En la hoja **Directivas de configuración de aplicaciones**, elija **Agregar**.
5.  En la hoja **Agregar directiva de configuración**, escriba un **nombre** y una **descripción** opcional para las opciones de configuración de aplicaciones.
6.  En **Tipo de inscripción del dispositivo**, elija **Aplicaciones administradas**.
7.  Elija **Seleccionar la aplicación requerida** y, después, en la hoja **Aplicaciones de destino**, elija **Managed Browser** o **Edge** para iOS, para Android o para ambos.
8.  Elija **Aceptar** para volver a la hoja **Agregar directiva de configuración**.
9.  Elija **Opciones de configuración**. En la hoja **Configuración**, defina los pares de clave y valor para proporcionar configuraciones para Managed Browser. Use las secciones posteriores de este artículo para obtener información sobre los diferentes pares de clave y valor que puede definir.
10. Cuando termine, elija **Aceptar**.
11. En la hoja **Agregar directiva de configuración**, elija **Agregar**.
12. Se crea la nueva configuración y se muestra en la hoja **Configuración de aplicación**.


## <a name="assign-the-configuration-settings-you-created"></a>Asignación de las opciones de configuración creadas

Debe asignar la configuración a los grupos de usuarios de Azure AD. Si ese usuario tiene instalada la aplicación de explorador protegido, esta se administra mediante la configuración especificada.

1. En la hoja **Aplicaciones cliente** del panel de administración de aplicaciones móviles de Intune, elija **Directivas de configuración de aplicaciones**.
2. En la lista de configuraciones de aplicación, seleccione la que desea asignar.
3. En la siguiente hoja, elija **Asignaciones**.
4. En la hoja **Asignaciones**, seleccione el grupo de Azure AD al que quiere asignar la configuración de aplicación y después elija **Aceptar**.


## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Configuración del proxy de aplicación para exploradores protegidos

Microsoft Edge e Intune Managed Browser y [Azure Active Directory Application Proxy]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) pueden usarse conjuntamente para admitir los siguientes casos de usuarios de dispositivos iOS y Android:

- Un usuario descarga e inicia sesión en la aplicación Microsoft Outlook. Las directivas de protección de aplicaciones de Intune se aplican automáticamente. Cifran los datos guardados e impiden que el usuario transfiera archivos corporativos a ubicaciones o aplicaciones no administradas en el dispositivo. Cuando el usuario hace clic en un vínculo a un sitio de intranet en Outlook, puede especificar que el vínculo se abra en la aplicación de explorador protegido en lugar de en otro explorador. El explorador protegido reconoce que este sitio de intranet se ha expuesto al usuario a través del proxy de aplicación. El usuario se enruta automáticamente a través del proxy de aplicación, para la autenticación con cualquier autenticación multifactor aplicable, y el acceso condicional antes de llegar al sitio de intranet. Este sitio, que anteriormente no se podía encontrar mientras el usuario fuera remoto, ahora es accesible y el vínculo en Outlook funciona según lo previsto.
- Un usuario remoto abre la aplicación de explorador protegido y se desplaza a un sitio de intranet con la dirección URL interna. El explorador protegido reconoce que este sitio de intranet se ha expuesto al usuario a través del proxy de aplicación. El usuario se enruta automáticamente a través del proxy de aplicación, para la autenticación con cualquier autenticación multifactor aplicable, y el acceso condicional antes de llegar al sitio de intranet. Este sitio, que anteriormente no se podía encontrar mientras el usuario fuera remoto, ahora es accesible.

### <a name="before-you-start"></a>Antes de empezar

- Configure las aplicaciones internas a través del proxy de aplicación de Azure AD.
    - Para configurar el proxy de aplicación y publicar aplicaciones, vea la [documentación de configuración](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). 
- Debe usar como mínimo la versión 1.2.0 de la aplicación Managed Browser.
- Los usuarios de las aplicaciones Managed Browser o Microsoft Edge tienen una [directiva de protección de aplicaciones de Intune](app-protection-policy.md) asignada a la aplicación.

    > [!NOTE]
    > Los datos de redireccionamiento actualizados del proxy de la aplicación pueden tardar hasta 24 horas en aplicarse a Managed Browser y a Microsoft Edge.


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Paso 1: Habilitar el redireccionamiento automático a un explorador protegido desde Outlook.
Outlook debe configurarse con una directiva de protección de aplicaciones que habilite el valor **Restringir contenido web para mostrar en Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>Paso 2: Asignar una directiva de configuración de aplicaciones para el explorador protegido.
Este procedimiento configura la aplicación Managed Browser o Microsoft Edge para usar el redireccionamiento del proxy de aplicación. Aplicando el procedimiento para crear una configuración de aplicaciones de Microsoft Edge o Managed Browser, proporcione el siguiente par de clave y valor:

| Key                                                             | Valor    |
|-----------------------------------------------------------------|----------|
| **com.microsoft.intune.mam.managedbrowser.AppProxyRedirection** | **true** |

Para más información sobre cómo usar Managed Browser, Microsoft Edge y Azure AD Application Proxy conjuntamente para tener un acceso fluido (y protegido) a las aplicaciones web locales, consulte la entrada de blog de Enterprise Mobility + Security [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Juntos mejor: Intune y Azure Active Directory unen fuerzas para mejorar el acceso de usuario).

> [!NOTE]
> Microsoft Edge usa los mismos pares de clave y valor que Managed Browser. 

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>Configuración de la página principal del explorador protegido

Este valor permite configurar la página principal que ven los usuarios cuando inician un explorador protegido o crean una pestaña nueva. 
- Esta configuración mostrará la página web en Managed Browser.  En su lugar, Microsoft Edge mostrará un acceso directo a la página principal.
- El icono del acceso directo a la página principal aparece como debajo del control de búsqueda.  No se puede editar ni eliminar.
- El acceso directo a la página principal mostrará el nombre de la organización para distinguirla.  Siempre aparecerá como el primer icono.

Aplicando el procedimiento para crear una configuración de aplicaciones de Microsoft Edge o Managed Browser, proporcione el siguiente par de clave y valor:

|                                Key                                |                                                           Valor                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Especifique una dirección URL válida. Las direcciones URL incorrectas se bloquean como medida de seguridad.<br>Ejemplo: `<https://www.bing.com>` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>Configuración de marcadores para un explorador protegido

Este valor permite configurar un conjunto de marcadores disponible para los usuarios de Microsoft Edge o Managed Browser.

- Los usuarios no pueden eliminar ni modificar estos marcadores
- Se muestran en la parte superior de la lista. Los marcadores creados por los usuarios aparecen debajo de estos marcadores.
- Si ha habilitado el redireccionamiento del proxy de aplicación, puede agregar aplicaciones web de proxy de aplicación mediante su dirección URL interna o externa.

Aplicando el procedimiento para crear una configuración de aplicaciones de Microsoft Edge o Managed Browser, proporcione el siguiente par de clave y valor:

|                                Key                                 |                                                                                                                                                                                                                                                         Valor                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | El valor de esta configuración es una lista de marcadores. Cada marcador consta del título y de la dirección URL del marcador. Separe el título y la dirección URL con el carácter <strong>&#124;</strong>.<br><br>Ejemplo:<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>Para configurar varios marcadores, separe cada par con el carácter doble <strong>&#124;&#124;</strong><br><br>Ejemplo:<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>Especificación de direcciones URL permitidas y bloqueadas para un explorador protegido

Aplicando el procedimiento para crear una configuración de aplicaciones de Microsoft Edge o Managed Browser, proporcione el siguiente par de clave y valor:

|Key|Valor|
|-|-|
|Elija de entre las siguientes opciones:<br><ul><li>Especifique direcciones URL permitidas (solo se permiten estas direcciones URL; no se puede acceder a ningún otro sitio):<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>Especifique direcciones URL bloqueadas (se puede acceder a todos los demás sitios):<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|El valor correspondiente de la clave es una lista de direcciones URL. Escriba todas las direcciones URL que quiera permitir o bloquear como un valor único, separadas por un carácter de barra vertical **&#124;**.<br><br>Ejemplos:<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>No especifique ambas claves. Si las dos claves están destinadas al mismo usuario, se usa la clave permitida, ya que se trata de la opción más restrictiva.
>Además, asegúrese de no bloquear páginas importantes como los sitios web de la empresa.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Formato de dirección URL para las direcciones URL permitidas y bloqueadas
Use la siguiente información para conocer los formatos permitidos y los caracteres comodín que puede usar al especificar direcciones URL en las listas de permitidos y bloqueados:

- Puede usar el carácter comodín (**&#42;**) según las reglas de la siguiente lista de patrones permitidos:

- Asegúrese de anteponer **http** o **https** a todas las direcciones URL al introducirlas en la lista.

- Puede especificar números de puerto en la dirección. Si no especifica un número de puerto, los valores usados son:

  -   Puerto 80 para http

  -   Puerto 443 para https

  No se admite el uso de caracteres comodín para el número de puerto. Por ejemplo, `http://www.contoso.com:;` y `http://www.contoso.com: /;` no se admiten.

- Use la siguiente tabla para obtener información sobre los patrones permitidos que puede usar al especificar direcciones URL:

|                  Dirección URL                  |                     Detalles                      |                                                Coincide                                                |                                No coincide                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              Coincide con una sola página               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              Coincide con una sola página               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | Coincide con todas las direcciones URL que comienzan por `www.contoso.com` |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     Coincide con todos los subdominios en contoso.com     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             Coincide con una sola carpeta              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  Coincide con una sola página, con un número de puerto   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          Coincide con una sola página segura           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    Coincide con una sola carpeta y todas sus subcarpetas    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

- Los siguientes son ejemplos de algunas de las entradas que no se pueden especificar:

  - `*.com`

  - `*.contoso/*`

  - `www.contoso.com/*images`

  - `www.contoso.com/*images*pigs`

  - `www.contoso.com/page*`

  - Direcciones IP

  - `https://*`

  - `http://*`

  - `http://www.contoso.com:*`

  - `http://www.contoso.com: /*`
## <a name="opening-links-within-the-intune-managed-browser-vs-microsoft-edge"></a>Apertura de vínculos dentro de Intune Managed Browser frente a Microsoft Edge 

Tanto Intune Managed Browser como Microsoft Edge ahora se consideran exploradores administrados por directivas o exploradores protegidos. Hoy en día, las directivas de protección de aplicaciones existentes dan como resultado que los vínculos web de las aplicaciones administradas de Intune se abran en un explorador concreto según el escenario y la plataforma. 

En Android: 
* Managed Browser se abrirá si un usuario tiene Managed Browser y Microsoft Edge descargados en el dispositivo. Para garantizar que se abre Microsoft Edge en lugar de Managed Browser, establezca la configuración de la aplicación "com.microsoft.intune.useEdge" en "true" para todas las aplicaciones administradas de Intune con un explorador administrado por directivas requerido.  
* Microsoft Edge se abrirá si solo Microsoft Edge se encuentra en el dispositivo y es el objetivo de la directiva.
* Managed Browser se abrirá si solo Managed Browser se encuentra en el dispositivo y es el objetivo de la directiva. 

En iOS, para aplicaciones que tienen integrado el SDK de Intune para iOS versión 9.0.9+: 
* Managed Browser si tanto Managed Browser como Edge están en el dispositivo, a menos que la opción de configuración de la aplicación "com.microsoft.intune.useEdge" esté establecida en "true" para todas las aplicaciones administradas de Intune con un explorador administrado por directivas requerido **o** Microsoft Edge si Microsoft Edge está instalado y ha recibido la directiva. 
* Microsoft Edge si solo Microsoft Edge se encuentra en el dispositivo y es objeto y ha recibido la directiva. 
* Managed Browser si solo Managed Browser se encuentra en el dispositivo y es objeto y ha recibido la directiva.

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>Cómo tener acceso a los registros de aplicación administrada con Managed Browser en iOS

Los usuarios finales que tengan Managed Browser instalado en el dispositivo iOS pueden ver el estado de administración de todas las aplicaciones publicadas de Microsoft. También pueden enviar registros para solucionar problemas con sus aplicaciones iOS administradas.

1. Abra la **Configuración** de iOS.
2. Seleccione la configuración de aplicación de del **explorador** administrado.
3. Cambie a **Habilitar diagnósticos de Intune** para establecer el explorador en modo de solución de problemas.
4. Abra el **explorador** administrado. Haga clic en **Ver estado de aplicación Intune** para revisar la configuración de directiva de aplicación individual.
5. Presione **Introducción** y **Compartir registros** o **Enviar registros a Microsoft** para enviar los registros de solución de problemas al administrador de TI o a Microsoft.

También puede abrir el explorador en modo de solución de problemas desde dentro de la aplicación.

1. Abra Managed Browser.
2. Escriba `about:intunehelp` en el cuadro de dirección.
El explorador se abre en modo de solución de problemas.

Para obtener una lista de las opciones de configuración almacenadas en los registros de la aplicación, consulte [Revisión de los registros de protección de aplicaciones en Managed Browser](app-protection-policy-settings-log.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Seguridad y privacidad de Managed Browser

-   Managed Browser no usa la configuración que realizan los usuarios para el explorador integrado en sus dispositivos. Managed Browser no puede acceder a esta configuración.

-   Si configura las opciones **Requerir PIN sencillo para el acceso** o **Requerir credenciales corporativas para el acceso** en una directiva de protección de aplicaciones asociada a Managed Browser, cuando un usuario seleccione el vínculo de ayuda en la página de autenticación, podrá ir a cualquier sitio de Internet independientemente de si se ha agregado a una lista de bloqueados de la directiva.

-   Managed Browser puede bloquear el acceso a sitios solo cuando se accede a estos directamente. No bloquea el acceso cuando se usan servicios intermedios (por ejemplo, un servicio de traducción) para acceder al sitio.

-   Para permitir la autenticación y acceder a la documentación de Intune, **&#42;.microsoft.com** está exento de la configuración de permitidos o bloqueados. Siempre está permitida.

### <a name="turn-off-usage-data"></a>Desactivar los datos de uso
Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso de Managed Browser para mejorar sus productos y servicios. Los usuarios pueden usar en sus dispositivos la configuración de **Datos de uso** para desactivar la recopilación de datos. No tiene ningún control sobre la recopilación de estos datos.

-   En dispositivos iOS, no se pueden abrir los sitios web que visitan los usuarios y que tienen un certificado expirado o que no es de confianza.

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) 
