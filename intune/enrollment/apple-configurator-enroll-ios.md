---
title: 'Inscripción de dispositivos iOS: Apple Configurator y el Asistente de configuración'
titleSuffix: Microsoft Intune
description: Aprenda a usar Apple Configurator para inscribir dispositivos iOS corporativos con el Asistente de configuración.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f80312c2bd82063ed0b61c36bef9b8bf4ae3e1aa
ms.sourcegitcommit: f26039d674eb4d61ab68264dd1a10b2e5e1d842c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74691795"
---
# <a name="set-up-ios-device-enrollment-with-apple-configurator"></a>Configuración de la inscripción de dispositivos iOS con Apple Configurator

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune permite la inscripción de dispositivos iOS con la herramienta [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344) desde un equipo Mac. La inscripción con Apple Configurator requiere que conecte mediante USB cada dispositivo iOS a un equipo Mac para configurar la inscripción corporativa. Puede inscribir dispositivos en Intune con Apple Configurator de dos maneras:
- **Inscripción con el Asistente de configuración**: borra el dispositivo y lo prepara para la inscripción mediante el Asistente de configuración.
- **Inscripción directa**: no borra el dispositivo y lo inscribe mediante la configuración de iOS. Este método solo admite dispositivos **sin afinidad de usuario**.

No se pueden usar los métodos de inscripción de Apple Configurator con el [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Requisitos previos

- Acceso físico a dispositivos iOS
- [Configurar entidad de MDM](../fundamentals/mdm-authority-set.md)
- [Un certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- Números de serie del dispositivo (solo inscripción mediante el Asistente de configuración)
- Cables de conexión USB
- Equipo macOS con [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Creación de un perfil de Apple Configurator para los dispositivos

Un perfil de inscripción de dispositivo define la configuración que se aplica durante la inscripción. Esta configuración se aplica una sola vez. Siga estos pasos para crear un perfil de inscripción para inscribir dispositivos iOS con Apple Configurator.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Apple Configurator**  > **Perfiles** > **Crear**.

    ![Creación de un perfil de Apple Configurator](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. En **Crear perfil de inscripción**, escriba un **nombre** y una **descripción** para el perfil con fines administrativos. Los usuarios no ven estos detalles. Puede usar este campo de nombre para crear un grupo dinámico en Azure Active Directory. Use el nombre de perfil para definir el parámetro enrollmentProfileName para asignar dispositivos con este perfil de inscripción. Obtenga más información sobre los grupos dinámicos de Azure Active Directory.

    ![Captura de pantalla de la pantalla de creación de perfil con inscripción con la afinidad de usuario seleccionada](./media/apple-configurator-enroll-ios/apple-configurator-profile-create.png)

3. En **Afinidad de usuario**, elija si los dispositivos con este perfil deben inscribirse con o sin un usuario asignado.

    - **Inscribir con afinidad de usuario**: seleccione esta opción para dispositivos que pertenezcan a usuarios y necesiten usar el portal de empresa para hacer uso de servicios, como instalar aplicaciones. El dispositivo se debe afiliar a un usuario con el Asistente de configuración y, después, se le puede permitir el acceso a los datos y al correo electrónico de la empresa. Solo se admite para la inscripción con el asistente para la configuración. Se necesita una afinidad de usuario [Punto de conexión mixto/nombre de usuario de WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Más información](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Inscribir sin afinidad de usuario**: seleccione esta opción para dispositivos no afiliados con un usuario único. Use esta opción para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de un usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio. Se requiere para la inscripción directa.

     > [!NOTE]
     > Cuando se seleccione **Inscribir con afinidad de usuario**, asegúrese de que el dispositivo se afilie a un usuario con el asistente de configuración en las primeras 24 horas del dispositivo que se está inscribiendo. De lo contrario, podría producirse un error en la inscripción y se necesitará un restablecimiento de fábrica para inscribir el dispositivo.

4. Si elige **Inscribir con afinidad de usuario**, tiene la opción de permitir que los usuarios se autentiquen en el portal de empresa en lugar de con el Asistente para configuración de Apple.

    > [!NOTE]
    > Si quiere realizar alguna de las acciones siguientes, establezca **Authenticate with Company Portal instead of Apple Setup Assistant** (Autenticar con el Portal de empresa en lugar del Asistente de configuración) en **Sí**.
    >    - usar la autenticación multifactor
    >    - pedir a los usuarios que cambien su contraseña cuando inician sesión por primera vez
    >    - pedir a los usuarios que restablezcan las contraseñas expiradas durante la inscripción
    >
    > Estas operaciones no se admiten durante la autenticación con el asistente de configuración de Apple.


6. Elija **Crear** para guardar el perfil.

## <a name="setup-assistant-enrollment"></a>Inscripción con el asistente para la configuración

### <a name="add-apple-configurator-serial-numbers"></a>Adición de números de serie de Apple Configurator

1. Cree una lista de valores separados por comas (.csv), con dos columnas, sin un encabezado. Agregue el número de serie en la columna izquierda y los detalles en la columna derecha. El número máximo actual de filas en la lista es de 5 000. En un editor de texto, la lista .csv tiene este aspecto:

    F7TLWCLBX196,detalles de dispositivo</br>
    DLXQPCWVGHMJ,detalles de dispositivo

   Obtenga información sobre [cómo buscar el número de serie de un dispositivo iOS](https://support.apple.com/HT204073).
2. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Apple Configurator**  > **Dispositivos** > **Agregar**.

5. Seleccione un **perfil de inscripción** para aplicarlo a los números de serie que se van a importar. Si desea que los detalles nuevos de número de serie sobrescriban los detalles existentes, elija **Sobrescribir detalles de identificadores existentes**.
6. En **Dispositivos de importación**, desplácese hasta el archivo .csv de los números de serie y seleccione **Agregar**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Reasignación de un perfil a los números de serie de los dispositivos

Puede asignar un perfil de inscripción al importar los números de serie de iOS para la inscripción de Apple Configurator. También puede asignar perfiles desde dos sitios en Azure Portal:
- **Dispositivos de Apple Configurator**
- **Perfiles de AC**

#### <a name="assign-from-apple-configurator-devices"></a>Asignación desde dispositivos de Apple Configurator
1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Apple Configurator** > **Dispositivos** > elija los números de serie > **Asignar perfiles**.
2. En **Asignar perfil**, elija el **Nuevo perfil** que quiera asignar y luego **Asignar**.

#### <a name="assign-from-profiles"></a>Asignación desde perfiles
1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Apple Configurator** > **Perfiles** y elija un perfil.
2. En el perfil, elija **Dispositivos asignados** y después elija **Asignar**.
3. Filtre para buscar los números de serie del dispositivo que quiera asignar al perfil, seleccione los dispositivos y elija **Asignar**.

### <a name="export-the-profile"></a>Exportación del perfil
Después de crear el perfil y asignar números de serie, debe exportar el perfil desde Intune como una dirección URL. Después, impórtelo en Apple Configurator en un equipo Mac para su implementación en dispositivos.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Apple Configurator** > **Perfiles** y elija el perfil para exportar.
2. En el perfil, seleccione **Exportar perfil**.
3. Copie la **dirección URL del perfil**. Puede agregarla a Apple Configurator para definir el perfil de Intune usado por los dispositivos iOS.

   Después, importe este perfil en Apple Configurator en el procedimiento siguiente para definir el perfil de Intune usado por dispositivos iOS.

### <a name="enroll-devices-with-setup-assistant"></a>Inscripción de dispositivos con el Asistente de configuración

1. En un equipo Mac, abra **Apple Configurator 2**. En la barra de menús, elija **Apple Configurator 2** y, después, elija **Preferencias**.
    > [!WARNING]
    > Los dispositivos se restablecen en la configuración de fábrica durante el proceso de inscripción. Como procedimiento recomendado, restablezca el dispositivo y enciéndalo. Los dispositivos deberían estar en la pantalla **Hola** cuando conecte el dispositivo.
    > Si el dispositivo ya se ha registrado con la cuenta de Id. de Apple, debe eliminarse de la iCloud de Apple antes de iniciar el proceso de inscripción. El mensaje de error indica que "no se puede activar [nombre de dispositivo]".

2. En el panel de **preferencias**, seleccione **Servidores** y elija el símbolo más (+) para iniciar el asistente del servidor MDM. Seleccione **Siguiente**.
3. Escriba el **nombre de host o la dirección URL** y la **dirección URL de inscripción** para el servidor MDM en el Asistente de configuración para la inscripción de dispositivos de iOS con Microsoft Intune. Para la dirección URL de inscripción, escriba la dirección URL del perfil de inscripción exportada desde Intune. Seleccione **Siguiente**.  
    Puede omitir de forma segura una advertencia que indica "no se comprueba la dirección URL del servidor". Para continuar, elija **Siguiente** hasta que finalice el asistente.
4. Conecte los dispositivos móviles iOS al equipo Mac con un adaptador USB.
5. Seleccione los dispositivos iOS que quiera administrar y, después, elija **Preparar**. En el panel **Prepare iOS Device** (Preparar el dispositivo iOS), seleccione **Manual** y luego elija **Siguiente**.
6. En el panel **Enroll in MDM Server** (Inscribir en servidor MDM), seleccione el nuevo servidor y elija **Siguiente**.
7. En el panel **Supervise Devices** (Supervisar dispositivos), seleccione el nivel de supervisión y luego elija **Siguiente**.
8. En el panel **Create an Organization** (Crear una organización), seleccione la **organización** o cree una nueva y luego elija **Siguiente**.
9. En el panel **Configure iOS Setup Assistant** (Configurar el Asistente de configuración de iOS), elija los pasos que se presentan al usuario y, después, elija **Preparar**. Si se le solicita, autentíquese para actualizar la configuración de confianza.  
10. Cuando el dispositivo iOS termine la preparación, desconecte el cable USB.  

### <a name="distribute-devices"></a>Distribuir los dispositivos
Los dispositivos ya están listos para la inscripción corporativa. Apague los dispositivos y distribúyalos a los usuarios. Cuando los usuarios enciendan sus dispositivos, se iniciará el Asistente de configuración.

Una vez que los usuarios reciban sus dispositivos, deberán completar el Asistente de configuración. Los dispositivos configurados con afinidad de usuario pueden instalar y ejecutar la aplicación del Portal de empresa para descargar aplicaciones y administrar dispositivos.

## <a name="direct-enrollment"></a>Inscripción directa
Cuando inscribe dispositivos iOS directamente con Apple Configurator, puede inscribir un dispositivo sin adquirir su número de serie. También puede nombrar el dispositivo con fines de identificación antes de que Intune capture el nombre del dispositivo durante la inscripción. No se admite la aplicación de portal de empresa para dispositivos inscritos directamente. Con este método no se borra el dispositivo.

Las aplicaciones que requieren la afiliación de un usuario no se pueden instalar, incluida la aplicación del Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportación del perfil como .mobileconfig a dispositivos iOS

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Apple Configurator** > **Perfiles** > elija el perfil para exportar > **Exportar perfil**.
2. En **Inscripción directa**, elija **Descargar perfil** y guarde el archivo. Un archivo de perfil de inscripción solo es válido durante dos semanas, momento en el que se debe volver a crear.
3. Transfiera el archivo a un equipo Mac en el que se ejecute [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) para poder transferir archivos directamente como un perfil de administración a dispositivos iOS.
4. Prepare el dispositivo con Apple Configurator mediante los pasos siguientes:
    1. En un equipo Mac, abra Apple Configurator 2.0.
    2. Conecte el dispositivo iOS al equipo Mac con un cable USB. Cierre Fotos, iTunes y otras aplicaciones que se abren en el dispositivo cuando se detecta el dispositivo.
    3. En Apple Configurator, elija el dispositivo iOS conectado y, después, elija el botón **Agregar**. Las opciones que se pueden agregar al dispositivo aparecen en la lista desplegable. Elija **Perfiles**.

        ![Captura de pantalla de Exportar perfil para Inscripción del Asistente de configuración con URL del perfil destacado](./media/apple-configurator-enroll-ios/ios-apple-configurator-add-profile.png)

    4. Use el selector de archivos para seleccionar el archivo .mobileconfig que ha exportado desde Intune y, después, elija **Agregar**. El perfil se agrega al dispositivo. Si el dispositivo es No supervisado, la instalación requiere la aceptación en el dispositivo.
5. Use los pasos siguientes para instalar el perfil en el dispositivo iOS. El dispositivo debe haber completado el Asistente de configuración y estar listo para usarse. Si la inscripción implica implementaciones de aplicaciones, el dispositivo debe tener un identificador de Apple configurado, porque la implementación de aplicaciones requieren que se disponga de un identificador de Apple con la sesión iniciada en App Store.
    1. Desbloquee el dispositivo iOS.
    2. En el cuadro de diálogo **Instalar el perfil** de **Perfil de administración**, elija **Instalar**.
    3. Proporcione el código de acceso del dispositivo o el identificador de Apple, si es necesario.
    4. Acepte la **advertencia** y elija **Instalar**.
    5. Acepte la **advertencia remota** y elija **Confiar**.
    6. Cuando el cuadro **Perfil instalado** confirme el perfil como Instalado, elija **Listo**.

6. En el dispositivo iOS, abra **Configuración** y vaya a **General**  > **Administración de dispositivos** > **Perfil de administración**. Confirme que aparece la instalación del perfil y compruebe las restricciones de directivas de iOS y las aplicaciones instaladas. Las aplicaciones y las restricciones de directivas pueden tardar hasta 10 minutos en aparecer en el dispositivo.

7. Distribuya los dispositivos. Ahora el dispositivo iOS está inscrito en Intune y administrado.





