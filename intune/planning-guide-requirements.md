---
title: "Determinación de los requisitos de los escenarios de casos de uso"
description: "Este artículo ayuda a determinar los requisitos de los escenarios de casos de subuso y de casos de uso de Intune para una implementación solo en la nube de Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8806dc965653deaca5ab370c290403ae049e5c58
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="determine-use-case-scenario-requirements"></a>Determinación de los requisitos de los escenarios de casos de uso

En esta sección se determinan los requisitos de cada grupo organizativo dentro de cada escenario de caso de uso. Este proceso ayuda a prepararse para las otras áreas de planeamiento de la implementación de Intune como la arquitectura y el diseño, la incorporación y la implementación. También puede ayudar a identificar posibles carencias y desafíos relacionados con su proyecto de implementación de Intune.

Puede tener diferentes conjuntos de requisitos para cada uno de sus escenarios de casos de subuso o uso y sus grupos organizativos y plataformas de dispositivos móviles asociados. Por ejemplo, puede que los requisitos de sus escenarios de casos de uso corporativos exijan la inscripción de dispositivos en Intune con un conjunto más restrictivo de configuraciones, como un PIN de seis caracteres o la deshabilitación de la copia de seguridad en la nube. El escenario de caso de uso "bring your own device" (BYOD), puede ser menos restrictivo y permitir un PIN de 4 caracteres y la copia de seguridad en la nube.

También puede tener grupos organizativos en el escenario de caso de uso corporativo que tengan diferentes conjuntos de requisitos (por ejemplo, configuración de PIN, perfil de VPN o Wi-Fi, aplicaciones implementadas, etc.). También, sus requisitos pueden determinarse mediante las funcionalidades de la plataforma de dispositivos móviles (por ejemplo, lector de huellas digitales, perfil de correo electrónico, etc.).

Estos son algunos ejemplos de requisitos de casos de uso de la organización, que muestran diferentes conjuntos de requisitos para cada escenario de casos de subuso o uso, grupo organizativo y plataforma de dispositivos móviles. También puede usar la tabla siguiente para especificar los requisitos de casos de uso de la organización:

| **Casos de uso** | **Casos de subuso** | **Grupos** | **Plataformas de dispositivos** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| Corporativos | Trabajador de la información | Recursos humanos, finanzas | iOS | Correo electrónico seguro, configuración de dispositivo, perfiles, aplicaciones |                                                          
| Corporativos | Ejecutivos | Recursos humanos, finanzas | iOS | Correo electrónico seguro, configuración de dispositivo, perfiles, aplicaciones |                                                         
| Corporativos | Pantalla completa | Venta directa | Android | Configuración de dispositivo, perfiles, aplicaciones |
| BYOD | Trabajador de la información | Marketing, ventas | iOS | Correo electrónico seguro, configuración de dispositivo, perfiles, aplicaciones |                                                         
| BYOD | Ejecutivos | Marketing, ventas | iOS | Correo electrónico seguro, configuración de dispositivo, perfiles, aplicaciones |

Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para especificar los requisitos de casos de uso y subuso de su organización.


## <a name="examples-of-requirements"></a>Ejemplos de requisitos

Estos son algunos ejemplos más que pueden usarse en la columna "Requisitos":

- **Correo electrónico seguro**
    - Acceso condicional para Exchange Online o local
    - Directivas de protección de aplicaciones de Outlook

- **Configuración del dispositivo**
    - Configuración de PIN con cuatro, seis caracteres
    - Restringir la copia de seguridad en la nube

- **Perfiles**
    - Wi-Fi
    - VPN
    - Correo electrónico (Windows 10 Mobile)

- **Aplicaciones**
    - Office 365 con directivas de protección de aplicaciones
    - Línea de negocio (LOB) con directivas de protección de aplicaciones

## <a name="next-section"></a>Sección siguiente

En la sección siguiente se proporcionan instrucciones sobre [cómo desarrollar un plan de implementación de Intune](planning-guide-rollout-plan.md).