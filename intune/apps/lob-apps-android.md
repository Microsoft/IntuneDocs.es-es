---
title: Incorporación de una aplicación de línea de negocio de Android a Microsoft Intune
description: Obtenga información sobre cómo agregar una aplicación de línea de negocio (LOB) de Android a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4c1f3d8b6b7edbf51ca2aaa681909e6c220de3c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507235"
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>Incorporación de una aplicación de línea de negocio de Android a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Una aplicación de línea de negocio (LOB) es aquella que se agrega a Intune desde un archivo de instalación de la aplicación. Este tipo de aplicación normalmente se escribe localmente. Intune instala la aplicación de línea de negocio en el dispositivo del usuario. 

> [!Note]
> Para más información sobre las aplicaciones de línea de negocio y la consola para desarrolladores de Google Play, consulte [Publicación de aplicaciones privadas (LOB) de Google Play administrado con la consola para desarrolladores de Google](apps-add-android-for-work.md?#managed-google-play-private-lob-app-publishing-using-the-google-developer-console). 

> [!Note]
> Para más información sobre los dispositivos Android for Work, consulte [Incorporación de aplicaciones de Google Play administrado a dispositivos de Android Enterprise con Intune](apps-add-android-for-work.md). 

## <a name="step-1-specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. En el panel **Intune**, seleccione **Aplicaciones cliente**.
3. En la carga de trabajo **Aplicaciones cliente**, seleccione **Administrar** > **Aplicaciones**.
4. Encima de la lista de aplicaciones, elija **Agregar**.
5. En el panel **Agregar aplicación**, seleccione **Aplicación de línea de negocio**.

## <a name="step-2-configure-the-app-package-file"></a>Paso 2: Configuración del archivo de paquete de aplicaciones

1. En el panel **Agregar aplicación**, seleccione **Archivo del paquete de aplicaciones**.
2. En el panel **Archivo del paquete de aplicaciones**, seleccione el botón Examinar. Luego, seleccione un archivo de instalación de Android con la extensión **.apk**.
3. Cuando haya terminado, seleccione **Aceptar**.

## <a name="step-3-configure-app-information"></a>Paso 3: Configuración de información de la aplicación

1. En el panel **Agregar aplicación**, seleccione **Información de la aplicación**.
2. En el panel **Información de la aplicación**, agregue los datos de su aplicación. Dependiendo de la aplicación que haya elegido, algunos de los valores de este panel podrían rellenarse automáticamente.
    - **Nombre**: escriba el nombre de la aplicación tal como aparece en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo aparece una de las aplicaciones en el portal de empresa.
    - **Descripción**: escriba una descripción de la aplicación. La descripción aparece en el portal de empresa.
    - **Publicador**: Escriba el nombre del publicador de la aplicación.
    - **Versión mínima del sistema operativo**: en la lista, elija la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Categoría**: seleccione una o varias de las categorías de aplicaciones integradas o seleccione una categoría que haya creado. Las categorías facilitan a los usuarios encontrar la aplicación cuando exploran el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: Muestra la aplicación de forma destacada en la página principal del portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL aparece en el portal de empresa.
    - **Dirección URL de privacidad**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL aparece en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación. Un ejemplo es **Departamento de Recursos Humanos**.
    - **Notas**: escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: cargue un icono que esté asociado a la aplicación. Este icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3. Cuando haya terminado, seleccione **Aceptar**.

## <a name="step-4-finish-up"></a>Paso 4: Finalizar

1. En el panel **Agregar aplicación**, compruebe que los detalles de la aplicación son correctos.
2. Seleccione **Agregar** para cargar la aplicación en Intune.

La aplicación que ha creado ahora aparece en la lista de aplicaciones. En la lista, puede asignar la aplicación a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

## <a name="step-5-update-a-line-of-business-app"></a>Paso 5: Actualización de una aplicación de línea de negocio

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

Si la opción **Check apps from external sources** (Comprobar aplicaciones de orígenes externos) está activada en el dispositivo Android, se le preguntará al usuario antes de instalar la actualización. De lo contrario, la actualización se instalará automáticamente.

> [!Note]
> Para que el servicio de Intune implemente correctamente un archivo APK nuevo en el dispositivo, se debe incrementar la cadena `android:versionCode` en el archivo AndroidManifest.xml del paquete APK.

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

- Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Consulte [Supervisión de información de aplicación y asignaciones con Microsoft Intune](apps-monitor.md).

- Obtenga más información sobre el contexto de la aplicación en Intune. Consulte [Información general sobre los ciclos de vida del dispositivo y la aplicación](../fundamentals/device-lifecycle.md).
