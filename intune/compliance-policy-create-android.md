---
title: Creación de una directiva de cumplimiento de dispositivos Android en Microsoft Intune - Azure | Microsoft Docs
description: Cree o configure una directiva de cumplimiento de dispositivos Microsoft Intune para dispositivos Android. Opte por permitir dispositivos con Jailbroken, establecer el nivel de amenaza aceptable, buscar Google Play, especificar la versión de sistema operativo mínima y máxima, elegir los requisitos de contraseña y permitir aplicaciones de instalación de prueba.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/19/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0dc4fc0a0f16717bd0c21db3a9e7e57daf7867bc
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069434"
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Incorporación de una directiva de cumplimiento de dispositivos para dispositivos Android en Intune

Una directiva de cumplimiento de dispositivos de Intune para Android especifica las reglas y la configuración que los dispositivos Android deben cumplir para que se consideren compatibles. Puede usar estas directivas con [acceso condicional](conditional-access.md) para permitir o bloquear el acceso a los recursos de la organización. También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento. 

Para más información sobre las directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

En este tema se enumeran los valores que puede usar en una directiva de cumplimiento para dispositivos Android.

## <a name="non-compliance-and-conditional-access"></a>Incumplimiento y acceso condicional

En la tabla siguiente se describe cómo administrar la configuración de no conformidad cuando se usa una directiva de cumplimiento con una directiva de acceso condicional.

--------------------

|**Configuración de directiva**| **Android 4.0 y versiones posteriores, Samsung Knox Standard 4.0 y versiones posteriores** |
| --- | ----|
| **Configuración de PIN o contraseña** |  En cuarentena |
| **Cifrado del dispositivo** | En cuarentena |
| **Dispositivo liberado o modificado** | En cuarentena (no es una configuración) |
| **Perfil de correo electrónico** | No disponible |
| **Versión de SO mínima** | En cuarentena |
| **Versión de SO máxima** |   En cuarentena |
| **Atestación de estado de Windows** | No disponible |

--------------------------

**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del dispositivo no exige cumplimiento. Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo. Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

  - El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
  - El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Para **Plataforma**, seleccione **Android**. 
5. Elija **Settings Configure** (Definir configuración). Especifique las opciones **Estado de dispositivos**, **Propiedades de dispositivo** y **Seguridad del sistema**, tal y como se describe en este artículo.

## <a name="device-health"></a>Device health

- **Dispositivos raíz**: elija **Bloquear** para marcar los dispositivos raíz (con jailbreak) como no conformes. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Requerir que el dispositivo tenga el nivel de amenaza del dispositivo**: use esta opción para hacer que la evaluación del riesgo de la solución Lookout MTP sea una condición para el cumplimiento. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración. Para usar esta configuración, elija el nivel de amenaza permitido:
  - **Protegido**: esta opción es la más segura y el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio:** el dispositivo se evalúa como compatible si las amenazas existentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto**: esta opción es la menos segura, ya que permite que todos los niveles de amenaza. Quizás sea útil si utiliza esta solución solo con fines informativos.
- **Google Play Services está configurado**: se **requiere** que la aplicación Google Play Services esté instalada y habilitada. Google Play Services permite actualizaciones de seguridad y es una dependencia de nivel base para muchas características de seguridad en los dispositivos de Google certificados. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Proveedor de seguridad actualizada**: se **requiere** que un proveedor de seguridad actualizado pueda proteger un dispositivo frente a vulnerabilidades conocidas. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Examen de amenazas en las aplicaciones**: se **requiere** que la característica **Verificar aplicaciones** de Android esté habilitada. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  > [!NOTE]
  > En la plataforma Android heredada, esta característica es una configuración de cumplimiento. Intune solo puede comprobar si esta configuración está habilitada en el nivel de dispositivo.

- **Atestación de dispositivo SafetyNet**: especifique el nivel de [atestación de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que se debe cumplir. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se evalúa el cumplimiento o incumplimiento de esta configuración.
  - **Comprobar integridad básica**
  - **Comprobar integridad básica y dispositivos certificados**

## <a name="device-property-settings"></a>Configuración de propiedades de dispositivo

- **Versión mínima del sistema operativo**: cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Se muestra un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo y luego acceder a los recursos de la empresa.
- **Versión máxima de SO**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa. Se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, el dispositivo no podrá acceder a los recursos de la empresa.

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: **requiere** que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Longitud mínima de la contraseña**: indique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.
- **Tipo de contraseña requerida**: elija si una contraseña debe incluir solo caracteres numéricos o una combinación de números y otros caracteres. Las opciones son:
  - **Valor predeterminado del dispositivo**
  - **Biométrico de seguridad baja**
  - **Al menos numérica** (valor predeterminado)
  - **Numérica compleja**: no se permiten números consecutivos ni repetidos (como `1111` o `1234`).
  - **Al menos alfabética** 
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: indique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Expiración de la contraseña (días)**: seleccione el número de días que faltan para que expire la contraseña y durante los cuales el usuario debe crear otra.
- **Número de contraseñas anteriores que no se pueden reutilizar**: indique el número de contraseñas recientes que no se pueden volver a usar. Utilice esta configuración para impedir que el usuario cree contraseñas usadas anteriormente.

### <a name="encryption"></a>Cifrado

- **Cifrado de almacenamiento de datos en un dispositivo** (Android 4.0 y versiones posteriores, o KNOX 4.0 y versiones posteriores): elija **Requerir** para cifrar el almacenamiento de datos en los dispositivos. Los dispositivos se cifran al elegir la opción **Requerir una contraseña para desbloquear dispositivos móviles**. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

### <a name="device-security"></a>Seguridad de dispositivos

- **Bloquear aplicaciones de orígenes desconocidos**: elija **bloquear** los dispositivos con la opción "Seguridad > Orígenes desconocidos" habilitada (se admite de Android 4.0 a Android 7.x; no se admite en Android 8.0 ni versiones posteriores). Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  Para realizar instalaciones de prueba de las aplicaciones, se deben permitir los orígenes desconocidos. Si no realiza instalaciones de prueba de las aplicaciones Android, establezca esta característica en **Bloquear** para habilitar esta directiva de cumplimiento. 

  > [!IMPORTANT]
  > Las aplicaciones de instalación de prueba requieren que se habilite la opción **Bloquear aplicaciones de orígenes desconocidos**. Aplique esta directiva de cumplimiento solo si no realiza instalaciones de prueba de las aplicaciones Android en dispositivos.

- **Integridad en tiempo de ejecución de la aplicación Portal de empresa**: elija **Requerir** para confirmar que la aplicación Portal de empresa cumple los siguientes requisitos:

  - Tiene instalado el entorno de tiempo de ejecución predeterminado.
  - Está firmada correctamente.
  - No se encuentra en modo de depuración.
  - Se ha instalado desde un origen conocido.

  Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

- **Bloquear depuración USB en el dispositivo** (Android 4.2 o versiones posteriores): elija **Bloquear** para evitar que los dispositivos usen la característica de depuración USB. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Nivel mínimo de revisión de seguridad** (Android 6.0 o posterior): seleccione el nivel de revisión de seguridad más antiguo que puede tener un dispositivo. Los dispositivos que no estén al menos en este nivel de revisión se consideran no conformes. La fecha debe especificarse en el formato `YYYY-MM-DD`.
- **Aplicaciones restringidas**: escriba el **Nombre de la aplicación** y el **Identificador de lote de aplicaciones** de las aplicaciones que deben estar restringidas. Seleccione **Agregar**. Un dispositivo con al menos una aplicación restringida instalada se marca como no conforme.

Cuando termine, seleccione **Aceptar** > **Aceptar** para guardar los cambios.

## <a name="locations"></a>Ubicaciones

En la directiva, realice una elección entre las ubicaciones existentes. ¿Aún no tiene una ubicación? En el apartado [Usar ubicaciones (límite de red) en Intune](use-network-locations.md) se proporcionan algunas instrucciones.

1. Elija **Ubicaciones**.
2. En la lista, compruebe la ubicación y elija **Seleccionar**.
3. Haga clic en **Guardar** la directiva.

## <a name="actions-for-noncompliance"></a>Acciones en caso de incumplimiento

Seleccione **Actions for noncompliance** (Acciones en caso no conformidad). La acción predeterminada marca inmediatamente el dispositivo como no conforme.

Puede cambiar la programación cuando el dispositivo se marca como no conforme, por ejemplo, después de un día. También puede configurar una segunda acción que envía un correo electrónico al usuario cuando el dispositivo es no conforme.

En [Adición de acciones en caso de incumplimiento](actions-for-noncompliance.md) se proporciona más información, por ejemplo, cómo crear un correo electrónico para notificar a los usuarios.

Por ejemplo, se usa la característica Ubicaciones y se agrega una ubicación en una directiva de cumplimiento. La acción predeterminada en caso de incumplimiento se aplica cuando se selecciona al menos una ubicación. Si el dispositivo no está conectado a las ubicaciones seleccionadas, se considera de inmediato como no conforme. Puede dar a los usuarios un período de gracia, por ejemplo, un día.

## <a name="scope-tags"></a>Etiquetas de ámbito

Las etiquetas de ámbito son una excelente manera de asignar directivas a grupos específicos, como Ventas, Ingeniería, RR. HH., etc. Puede agregar etiquetas de ámbito a las directivas de cumplimiento. Vea [Uso de etiquetas de ámbito para filtrar directivas](scope-tags.md). 

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

Una vez que se crea una directiva, no hace nada hasta que se asigna. Para asignar la directiva: 

1. Elija una directiva que haya configurado. Las directivas existentes están en **Conformidad de dispositivos** > **Directivas**.
2. Elija la directiva y luego **Asignaciones**. Puede incluir o excluir grupos de seguridad de Azure Active Directory (AD).
3. Elija **Grupos seleccionados** para ver los grupos de seguridad de Azure AD. Seleccione los grupos de usuarios a los que quiera aplicar esta directiva y elija **Guardar** para implementar la directiva a los usuarios.

Ya ha aplicado la directiva a los usuarios. Se evalúa el cumplimiento de los dispositivos que utilizan los usuarios a los que se destina la directiva.

## <a name="next-steps"></a>Pasos siguientes
[Automatización del correo electrónico y adición de acciones para dispositivos no compatibles: Intune](actions-for-noncompliance.md)  
[Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)  
[Configuración de directivas de cumplimiento para Android Enterprise](compliance-policy-create-android-for-work.md)
