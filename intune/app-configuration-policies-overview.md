---
title: Directivas de configuración de aplicaciones para Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo usar las directivas de configuración de aplicaciones en un dispositivo iOS o Android en Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10dad24ee41f63dcc304d95e9b733f7de3f1b71a
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2019
ms.locfileid: "67649019"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Directivas de configuración de aplicaciones para Microsoft Intune

Use las directivas de configuración de aplicaciones de Microsoft Intune para proporcionar valores de configuración para una aplicación para iOS o Android. Estos valores de configuración permiten personalizar una aplicación mediante el uso de un enfoque estándar del sector para la configuración y administración de aplicaciones. La configuración de directivas de configuración se usa cada vez que la aplicación comprueba dichas directivas, que suele ser la primera vez que se ejecuta.

Puede asignar una directiva de configuración de aplicación a un grupo de usuarios y dispositivos mediante una combinación de asignaciones de inclusión y exclusión. Tras agregar una directiva de configuración de aplicación, podrá establecer las asignaciones de la directiva de configuración de aplicación. Al establecer las asignaciones de la directiva, puede elegir si quiere incluir o excluir los grupos de usuarios a los que se aplica la directiva. Si decide incluir uno o varios grupos, puede optar por seleccionar grupos específicos para incluir o seleccionar los grupos integrados. Los grupos integrados incluyen **Todos los usuarios**, **Todos los dispositivos** y **Todos los usuarios + todos los dispositivos**.

Por ejemplo, para una aplicación podría ser necesario especificar uno de estos detalles:

- Un número de puerto personalizado
- Configuración de idioma
- Configuración de seguridad
- Configuración de marca, como un logotipo de empresa

Si los usuarios indicaran esta configuración, podrían hacerlo incorrectamente, lo que aumentaría la carga del departamento de soporte técnico y ralentizaría la adopción de nuevas aplicaciones.

Las directivas de configuración de aplicaciones pueden ayudarle a eliminar los problemas de configuración de aplicaciones, ya que permiten asignar la configuración a una directiva que se asigna a los usuarios antes de ejecutar la aplicación. A continuación, la configuración se proporciona de forma automática y los usuarios no tienen que realizar ninguna acción.

Los valores de configuración se usan cada vez que la aplicación los busca. Normalmente, una aplicación busca opciones de configuración la primera vez que el usuario ejecuta la aplicación.

Tiene dos opciones sobre cómo usar las configuraciones de aplicación con Intune:
 - **Dispositivos administrados**: el dispositivo se administra mediante Intune como el proveedor de administración de dispositivos móviles (MDM).
 - **Aplicaciones administradas**: una aplicación se administra sin la inscripción de dispositivos.

> [!NOTE]
> Como administrador de Microsoft Intune, puede controlar qué cuentas de usuario se agregan a las aplicaciones de Microsoft Office en dispositivos administrados. Puede limitar el acceso solo a las cuentas de usuario de la organización permitidas y bloquear las cuentas personales en los dispositivos inscritos. Las aplicaciones auxiliares procesan la configuración de la aplicación y quitan y bloquean las cuentas no aprobadas.

## <a name="apps-that-support-app-configuration"></a>Aplicaciones que admiten la configuración de aplicaciones

### <a name="managed-devices"></a>Dispositivos administrados
Puede usar las directivas de configuración de aplicaciones en las aplicaciones que lo admitan. Para admitir la configuración de aplicaciones en Intune, las aplicaciones deben haberse escrito para este fin, tal como lo define la [Appconfig Community](https://www.appconfig.org/members). Consulte con el proveedor de su aplicación para obtener más información.

### <a name="managed-apps"></a>Aplicaciones administradas
Puede preparar las aplicaciones de línea de negocio incorporando Intune App SDK en la aplicación o encapsulando la aplicación después de que haberla desarrollado. El SDK de aplicaciones de Intune, disponible para iOS y Android, habilita su aplicación para las directivas de configuración de protección de aplicaciones de Intune. Su objetivo es minimizar la cantidad de cambios de código que debe realizar el desarrollador de la aplicación. Para obtener más información, vea [Información general del SDK para aplicaciones de Intune](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Compatibilidad de Graph API para la configuración de aplicaciones

Además, puede usar Graph API para realizar tareas de configuración de aplicaciones. Para obtener más información, consulte la [referencia sobre Graph API para la configuración de destino de MAM](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Pasos siguientes

### <a name="managed-devices"></a>Dispositivos administrados

 - Obtenga información sobre cómo usar la configuración de aplicaciones con los dispositivos iOS.  Consulte [Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados](app-configuration-policies-use-ios.md).
 - Obtenga información sobre cómo usar la configuración de aplicaciones con los dispositivos Android.  Vea [Agregar directivas de configuración de aplicaciones para dispositivos Android administrados](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Aplicaciones administradas

 - Obtenga información sobre cómo usar la configuración de aplicaciones con aplicaciones administradas. Consulte [Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos](app-configuration-policies-managed-app.md).
