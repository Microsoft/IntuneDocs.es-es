---
title: "Qué es la administración de aplicaciones | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: use este tema para conocer los aspectos básicos sobre la administración de aplicaciones con Microsoft Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 56eefde5969f5426886c07bd6e9a548c8526e82e
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="what-is-microsoft-intune-app-management"></a>¿Qué es la administración de aplicaciones de Microsoft Intune?


[!INCLUDE[azure_preview](./includes/azure_preview.md)]


Como administrador de TI, es probable que le hayan asignado la tarea de asegurarse de que los usuarios finales tengan acceso a las aplicaciones que necesitan para cumplir con su trabajo. Esto puede ser difícil por las siguientes causas:
- La amplia variedad de plataformas de dispositivo y tipos de aplicaciones.
- La necesidad de administrar aplicaciones de los dispositivos de la empresa así como de los propios dispositivos de los usuarios.
- Y todo ello garantizando que la red y los datos permanezcan seguros. 

Aparte de todo esto, puede que quiera asignar y administrar aplicaciones en dispositivos que no están inscritos en Intune.

Intune ofrece diversas funcionalidades para ayudarle a conseguir las aplicaciones que necesita y en los dispositivos de su elección.

## <a name="app-management-capabilities-by-platform"></a>Funcionalidades de administración de aplicaciones por plataforma

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8,1|Windows 10|
|Agregar y asignar aplicaciones a dispositivos y usuarios|Sí|Sí|Sí|Sí|
|Asignar aplicaciones a dispositivos no inscritos en Intune|Sí|Sí|No|No|
|Usar directivas de configuración de aplicaciones para controlar el comportamiento de inicio de las aplicaciones|No|Sí|No|No|
|Usar directivas de aprovisionamiento de aplicaciones móviles para renovar aplicaciones caducadas|No|Sí|No|No|
|Proteger los datos de empresa de las aplicaciones con directivas de protección de aplicaciones|Sí|Sí|No|No<sup>1</sup>|
|Quitar solo los datos corporativos de una aplicación instalada (eliminación selectiva de aplicaciones)|Sí|Sí|Sí|Sí|
|Supervisar las asignaciones de aplicaciones|Sí|Sí|Sí|Sí|
|Asignar y realizar el seguimiento de aplicaciones compradas por volumen desde una tienda de aplicaciones|No|No|No|Sí|
|Instalación obligatoria de aplicaciones en dispositivos (requerido)<sup>2</sup>|Sí|Sí|Sí|Sí|
|Instalación opcional en dispositivos desde el Portal de empresa (instalación disponible)|Sí|Sí|Sí|Sí|
|Instalar un acceso directo a una aplicación en Web (clip de web)|Sí|Sí|Sí|Sí|
|Aplicaciones internas (línea de negocio)|Sí|Sí|No|No|
|Aplicaciones de una tienda|Sí|Sí|Sí|Sí|
|Actualizar aplicaciones|Sí|Sí|Sí|Sí|

<sup>1</sup> Considere la opción de usar Windows Information Protection para proteger aplicaciones en dispositivos que ejecutan Windows 10.

<sup>1</sup>Se aplica solo a dispositivos administrados por Intune.


## <a name="how-to-get-started"></a>Cómo empezar

Encontrará la mayoría de las tareas relacionadas con las aplicaciones en la carga de trabajo **Mobile Apps** a la que puede acceder de la manera siguiente:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Mobile apps**.

    ![La carga de trabajo Mobile Apps](./media/apps-workload.png)

### <a name="manage"></a>Administrar
- **Aplicaciones**: aquí es donde podrá agregar, asignar y supervisar la mayoría de las aplicaciones. 
    - [Agregar aplicaciones](apps-add.md)
    - [Asignar aplicaciones](apps-deploy.md)
    - [Supervisión de aplicaciones](apps-monitor.md)
- **Directivas de configuración de aplicaciones**: estas directivas le permiten suministrar valores de configuración que podrían ser necesarios cuando un usuario ejecuta una aplicación. Si desea obtener información detallada, consulte:
    - [Directivas de configuración de aplicaciones](app-configuration-policies.md)
- **Directivas de protección de aplicaciones**: estas directivas permiten asociar valores de configuración con una aplicación con el fin de ayudar a proteger los datos de empresa que esta usa. Por ejemplo, podría restringir las funcionalidades de una aplicación para comunicarse con otras aplicaciones o pedir que el usuario escribiera un PIN para acceder a una aplicación de la empresa.
    - [Directivas de protección de aplicaciones](app-protection-policies.md)
- **Borrado selectivo de aplicaciones**: quita solamente los datos corporativos del dispositivo de usuario seleccionado.
    - [Borrado selectivo de aplicaciones](apps-selective-wipe.md)
- **Perfiles de aprovisionamiento de iOS**: las aplicaciones iOS incluyen un perfil y un código de aprovisionamiento que está firmado por un certificado. Cuando el certificado expira, ya no se puede ejecutar la aplicación. Intune proporciona las herramientas para asignar proactivamente una nueva directiva de perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima.
    - [Perfiles de aprovisionamiento de aplicaciones iOS](app-provisioning-profile-ios.md)

### <a name="monitor"></a>Supervisión
- **Aplicaciones con licencia**: vea, asigne y supervise las aplicaciones compradas por volumen de las tiendas de aplicaciones.
    - [Aplicaciones adquiridas por volumen de la Tienda Windows para empresas](windows-store-for-business.md)
- **Discovered Apps** (Aplicaciones detectadas): muestra todas las aplicaciones que asignó Intune y que están instaladas en un dispositivo.
- **App Install Status** (Estado de instalación de aplicación): muestra el estado de una asignación de aplicación que ha creado.
- **App protection status** (Estado de protección de aplicación): muestra el estado de una directiva de protección de aplicaciones de un usuario seleccionado.

Para más información, consulte [Supervisión de aplicaciones](apps-monitor.md).

### <a name="setup"></a>Setup
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](vpp-apps-ios.md) --->
- **Tienda Windows para empresas**: configure la integración con la Tienda Windows para empresas. Luego, puede sincronizar las aplicaciones adquiridas en Intune, asignarlas y realizar el seguimiento de su uso de licencias. 
    - [Aplicaciones adquiridas por volumen de la Tienda Windows para empresas](windows-store-for-business.md)
- **Company Portal branding** (Personalización de marca del Portal de empresa): personalice el Portal de empresa para adaptarlo a su empresa. 
    - [Configuración del Portal de empresa](company-portal-app.md)
