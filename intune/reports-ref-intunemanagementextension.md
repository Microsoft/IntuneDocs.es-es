---
title: Entidad IntuneManagementExtension
titleSuffix: Microsoft Intune
description: Tema de referencia sobre la categoría de entidad IntuneManagementExtension de las colecciones de entidades de la API de almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 934742108effda0a88f4bcc42e06daa12c55288c
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648837"
---
# <a name="reference-for-intune-management-extension"></a>Referencia de la extensión de administración de Intune

La categoría **IntuneManagementExtension** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la siguiente:

  - Versiones de una entidad IntuneManagementExtension
  - Estado de instalación de una entidad IntuneManagementExtension

## <a name="intunemanagementextensionversion"></a>IntuneManagementExtensionVersion

La entidad **IntuneManagementExtensionVersion** muestra todas las versiones usadas por IntuneManagementExtension.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| ExtensionVersionKey |Identificador único de la versión de IntuneManagementExtension. | 1 |
| ExtensionVersion |Número de versión de 4 dígitos. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstate"></a>IntuneManagementExtensionHealthState

**IntuneManagementExtensionHealthState** muestra todos los estados de mantenimiento posibles de la entidad IntuneManagementExtension.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| ExtensionStateKey |Identificador único del estado de mantenimiento. | 2 |
| ExtensionState |Estado de mantenimiento de una entidad IntuneManagementExtension. | Correcto |

## <a name="intunemanagementextension"></a>IntuneManagementExtension

**IntuneManagementExtension** muestra los estados de mantenimiento de IntuneManagementExtension de cada dispositivo Windows 10 cada día.
Los datos se conservan durante 60 días. 


|      Propiedad       |                         Descripción                         | Ejemplo |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               Identificador único de la fecha.                |   123   |
|      TenantKey      |              Identificador único del inquilino.               |   456   |
|      DeviceKey      |              Identificador único del dispositivo.               |   789   |
| ExtensionVersionKey | Identificador único de la versión de IntuneManagementExtension. |    1    |
|  ExtensionStateKey  |             Identificador único del estado de mantenimiento.              |    2    |

