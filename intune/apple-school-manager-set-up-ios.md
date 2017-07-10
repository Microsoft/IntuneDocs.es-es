---
title: "Configuración de la inscripción en el programa de Apple School Manager para dispositivos iOS"
titleSuffix: Intune on Azure
description: "Obtenga información sobre cómo configurar la inscripción en el programa de Apple School Manager para dispositivos iOS corporativos con Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73556209c88759ffe0747d9927cbcbb49600e0c0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Habilitación de la inscripción de dispositivos iOS con Apple School Manager

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tema ayuda a los administradores de TI a habilitar la inscripción de dispositivos iOS adquiridos mediante el programa de [Apple School Manager](https://school.apple.com/) (ASM). Microsoft Intune puede implementar un perfil de inscripción "de forma inalámbrica" que inscriba los dispositivos de ASM en la administración. El administrador no tiene que tocar nunca cada dispositivo administrado. Un perfil de ASM contiene la configuración de administración que se aplica a los dispositivos durante la inscripción, incluidas las opciones del Asistente de configuración.

**Pasos para la inscripción de ASM**
1. [Obtener un token de ASM y asignar los dispositivos](#get-the-asm-token-and-assign-devices)
2. [Crear un perfil de inscripción](#create-an-apple-enrollment-profile)
3. [Conectar School Data Sync](#connect-school-data-sync) (opcional)
4. [Sincronización de dispositivos administrados por ASM](#sync-asm-managed-devices)
5. [Asignar el perfil de ASM a los dispositivos](#assign-an-asm-profile-to-devices)
6. [Distribuir los dispositivos a los usuarios](#distribute-devices-to-users)

>[!NOTE]
>No se puede usar la inscripción en ASM con el [Programa de inscripción de dispositivos (DEP)](device-enrollment-program-enroll-ios.md) de Apple ni con la cuenta del [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md) de Apple.

## <a name="get-the-apple-asm-token-and-assign-devices"></a>Obtener un token de ASM y asignar los dispositivos

Antes de poder inscribir dispositivos iOS corporativos en Apple School Manager (ASM), necesita un archivo de token (.p7m) de ASM de Apple. Este token permite a Intune sincronizar información sobre dispositivos que participan en ASM. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles. En Azure Portal, también puede asignar números de serie a los dispositivos para su administración.

**Requisitos previos**
- [Certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- Suscribirse a [Apple School Management](http://school.apple.com)

**Paso 1. Descargue un certificado de clave pública de Intune necesario para crear un token de ASM de Apple.**<br>
1. En el [portal de Intune](https://aka.ms/intuneportal) de Azure, elija **Inscripción de dispositivos** y después seleccione **Token del Programa de inscripción**.
2. En la hoja **Token del Programa de inscripción**, seleccione **Descargar la clave pública** para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal de Apple School Manager.

**Paso 2. Descargue un token de ASM y asigne los dispositivos.**<br>
Seleccione **Crear un token mediante Apple School Manager** e inicie sesión con su identificador de empresa de Apple. Puede usar este identificador de Apple para renovar el token de ASM.

   1.  En el [portal de Apple School Manager](https://school.apple.com), vaya a **MDM Servers** (Servidores MDM) y luego seleccione **Add MDM Server** (Agregar servidor MDM) (en la parte superior derecha).
   2.  Escriba el **nombre del servidor de MDM**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.
   3.  Seleccione **Upload File...** en el portal de Apple, examine el archivo .pem y seleccione **Save MDM Server** (Guardar servidor MDM) (en la parte inferior derecha).
   4.  Seleccione **Get Token** (Obtener token) y luego descargue el archivo de token del servidor (.p7m) en el equipo.
   5. Vaya a **Device Assignments** (Asignaciones de dispositivos) y **Choose Device** (Elegir dispositivo) con la entrada manual de **números de serie** o **números de pedido** o con la opción **Upload CSV File** (Cargar archivo CSV).
   6.   Elija la acción **Assign to Server** (Asignar al servidor) y seleccione el **servidor MDM** que creó.
   7. Especifique cómo va a **elegir los dispositivos** y luego proporcione información del dispositivo y especifique los detalles de cada dispositivo, como **Número de serie**y **Número de pedido**, o seleccione **Cargar archivo CSV**.
   8. Elija **Assign to Server** (Asignar al servidor), elija el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y después elija **Aceptar**.

**Paso 3. Escriba el identificador de Apple usado para crear el token de ASM.**<br>Este identificador debe usarse para renovar el token de ASM de Apple y guardarse para futuras referencias.

**Paso 4. Busque y cargue el token.**<br>
Vaya al archivo de certificado (.p7m), elija **Abrir** y luego seleccione **Cargar**. Intune sincroniza automáticamente los dispositivos de ASM desde Apple.

## <a name="create-an-apple-enrollment-profile"></a>Creación de un perfil de inscripción de Apple
Un perfil de inscripción de dispositivos define la configuración que se aplica a un grupo de dispositivos durante la inscripción.

1. En el portal de Intune, elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
2. En **Programa de inscripción**, seleccione **Perfiles del Programa de inscripción**.
3. En la hoja **Perfiles del Programa de inscripción**, seleccione **Crear**.
4. En la hoja **Crear perfil de inscripción**, escriba un **nombre** y una **descripción** para el perfil que se muestra en el portal de Intune.
5. En **Afinidad de usuario**, elija si los dispositivos con este perfil se inscribirán con o sin afinidad de usuario.

 - **Inscribir con afinidad de usuario**: el dispositivo se debe afiliar a un usuario durante la configuración inicial y luego se le puede permitir el acceso a los datos y al correo electrónico de la empresa. Elija la afinidad de usuario para los dispositivos administrados por ASM en los que los usuarios se registran con su identificador de Apple administrado.

 >[!NOTE]
 >La autenticación multifactor (MFA) no funciona durante la inscripción en dispositivos ASM con afinidad de usuario. Después de la inscripción, MFA funciona según lo previsto en estos dispositivos.

  El modo iPad compartido de Apple School Manager requiere la inscripción del usuario con afinidad de usuario.

 >[!NOTE]
    >ASM con afinidad de usuario precisa que el [punto de conexión WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) esté habilitado para solicitar el token de usuario. [Obtenga más información sobre WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Inscribir sin afinidad de usuario**: el dispositivo no está afiliado a ningún usuario. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afinidad de usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.

6. Seleccione **Configuración de administración de dispositivos**. Estos elementos se establecen durante la activación y requieren un restablecimiento de fábrica para los cambios. Configure las siguientes opciones de perfil y, a continuación, seleccione **Guardar**:

    - **Supervisado**: un modo de administración que permite más opciones de administración y deshabilita el bloqueo de activación de forma predeterminada. Si deja en blanco la casilla, tendrá funcionalidades de administración limitadas.

    - **Inscripción bloqueada** (requiere el modo de administración Supervisado): deshabilita la configuración de iOS que podría permitir la eliminación del perfil de administración. Si deja en blanco la casilla, permite que se quite el perfil de administración en el menú Configuración.

  - **iPad compartido**: (requiere los modos **Inscribir con afinidad de usuario** y **Supervisado**). Permite que varios usuarios inicien sesión en iPad inscritos mediante la utilización de un identificador de Apple administrado. Los identificadores de Apple administrados se crean en el portal de Apple School Manager.

  >[!NOTE]
  >Si el modo **iPad compartido** está deshabilitado en un perfil y los modos **Afinidad de usuario** o **Supervisado** se **desactivan**, el modo iPad compartido se deshabilita para el perfil de inscripción.

  - **Número máximo de usuarios en caché**: (requiere **iPad compartido** = **Sí**) crea una partición en el dispositivo para cada usuario. El valor recomendado es el número de alumnos con probabilidades de usar el dispositivo durante un período de tiempo. Por ejemplo, si seis alumnos usan el dispositivo con regularidad durante la semana, defina este número en seis.  

    - **Permitir emparejamiento**: especifica si se pueden sincronizar dispositivos iOS con equipos. Si elige **Permitir Apple Configurator mediante certificado**, debe seleccionar un certificado en **Certificado de Apple Configurator**.

    - **Certificados de Apple Configurator**: si eligió **Permitir Apple Configurator mediante certificado** en **Permitir emparejamiento**, seleccione un certificado de Apple Configurator para importar.

7. Seleccione **Valores del Asistente de configuración**, configure las siguientes opciones de perfil y, a continuación, seleccione **Guardar**:

    - **Department Name** (Nombre de departamento): aparece cuando los usuarios pulsan **About Configuration** (Acerca de la configuración) durante la activación.

    - **Teléfono del departamento**: aparece cuando el usuario hace clic en el botón Necesito ayuda durante la activación.
    - **Opciones del Asistente para la configuración**: si se excluyen de las opciones del Asistente de configuración, se pueden definir más adelante en el menú **Configuración** de iOS.
        - **Código de acceso**: solicita el código de acceso durante la activación. Solicite siempre un código de acceso, a menos que el dispositivo esté protegido o tenga el acceso controlado de otra manera (es decir, modo de quiosco que restringe el dispositivo a una aplicación).
        - **Servicios de ubicación**: si está habilitado, el Ayudante para la configuración solicitará el servicio durante la activación.
        - **Restauración**: si está habilitado, el Ayudante para la configuración solicitará una copia de seguridad de iCloud durante la activación.
        - **Id. de Apple**: si está habilitado, iOS solicita a los usuarios un identificador de Apple cuando Intune intenta instalar una aplicación sin un identificador. Se requiere un identificador de Apple para descargar aplicaciones del App Store de iOS, incluidas las que instala Intune.
        - **Términos y condiciones**: si está habilitado, el Asistente para la configuración solicita a los usuarios que acepten los términos y condiciones de Apple durante la activación.
        - **Touch ID**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Apple Pay**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Zoom**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Siri**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Datos de diagnóstico**: si esta opción está habilitada, el Ayudante de configuración solicitará este servicio durante la activación.

8. Para guardar la configuración del perfil, seleccione **Crear** en la hoja **Crear perfil de inscripción**.

## <a name="connect-school-data-sync"></a>Conectar con School Data Sync
(Opcional) ASM admite la sincronización de datos de lista de clase con Azure Active Directory (AD) mediante Microsoft School Data Sync (SDS). Complete los pasos siguientes para usar SDS para sincronizar los datos educativos.

1. En la hoja **Token del Programa de inscripción**, seleccione el banner informativo azul o **Conectar con SDS**.
2. Seleccione la opción **Permitir que Microsoft School Data Sync use este token**, establecida en **Permitir**. Esta configuración permite a Intune conectarse con SDS en Office 365.
3. Para habilitar una conexión entre ASM y Azure AD, seleccione **Configurar Microsoft School Data Sync**. Obtenga más información sobre [cómo configurar School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
4. Haga clic en **Aceptar** para guardar y continuar.

## <a name="sync-asm-managed-devices"></a>Sincronización de dispositivos administrados por ASM
Ahora que se ha concedido permiso a Intune para administrar los dispositivos de ASM, puede sincronizar Intune con el servicio de ASM para ver los dispositivos administrados en el portal de Intune.

1. En el portal de Intune, elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
2. En **Dispositivos del Programa de inscripción**, seleccione **Sincronizar**. La barra de progreso muestra la cantidad de tiempo que debe esperar antes de solicitar de nuevo la sincronización.

    Para cumplir con las condiciones de Apple relativas a un tráfico ASM aceptable, Intune impone las restricciones siguientes:
     -  Una sincronización completa de ASM no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune actualiza todos los números de serie que Apple ha asignado a Intune, independientemente de si el número de serie se ha sincronizado previamente o no. Si se intenta efectuar una sincronización completa sin que hayan pasado siete días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.
     -  Las solicitudes de sincronización tardan 15 minutos en finalizar. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón **Sincronización** está deshabilitado.

>[!NOTE]
>También puede asignar números de serie de ASM a los perfiles en la hoja **Dispositivos del Programa de inscripción**.

## <a name="assign-an-asm-profile-to-devices"></a>Asignación de un perfil de ASM a los dispositivos
Los dispositivos de ASM administrados por Intune deben tener un perfil de ASM asignado antes de la inscripción.

1. En el portal de Intune, elija **Inscripción de dispositivos** > **Inscripción de Apple** y luego seleccione **Perfiles del Programa de inscripción**.
2. En la lista de **Perfiles del Programa de inscripción**, seleccione el perfil que quiere asignar a los dispositivos y luego seleccione **Device Assignments** (Asignaciones de dispositivos).
3. Seleccione **Asignar** y, a continuación, seleccione los dispositivos de ASM que desea asignar a este perfil. Puede filtrar para ver los dispositivos de ASM disponibles:
  - **sin asignar**
  - **cualquiera**
  - **&lt;Nombre de perfil de ASM&gt;**
4. Seleccione los dispositivos que desea asignar. La casilla que se encuentra encima de la columna selecciona hasta 1000 dispositivos enumerados. Haga clic en **Asignar**. Para inscribir más de 1000 dispositivos, repita los pasos de la asignación hasta que todos los dispositivos tengan un perfil de ASM asignado.

## <a name="distribute-devices-to-users"></a>Distribuir los dispositivos a los usuarios

Ahora puede distribuir dispositivos corporativos a los usuarios. Cuando se activa un dispositivo iOS en ASM, se inscribe para que Intune lo administre. Si el dispositivo se ha activado y está en uso, el perfil no se aplicará hasta que el dispositivo se restablezca a sus valores de fábrica.

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Cómo los usuarios instalan y usan el Portal de empresa en sus dispositivos

Los dispositivos configurados con afinidad de usuario pueden instalar y ejecutar la aplicación del portal de empresa para descargar aplicaciones y administrar dispositivos. Después de que los usuarios reciben los dispositivos, deben ejecutar el Asistente de configuración e instalar la aplicación de Portal de empresa.