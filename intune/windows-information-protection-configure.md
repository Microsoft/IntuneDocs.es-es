---
title: Configuración de Windows Information Protection en Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre la configuración de Microsoft Intune que puede usar para administrar Windows Information Protection.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fc3684a04611e0b7ec8cd17cb5cdf428c1150a55
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570382"
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Configuración de Windows Information Protection en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Con el aumento en las empresas de dispositivos que pertenecen a los empleados, existe también un riesgo mayor de pérdidas accidentales de datos a través de aplicaciones y servicios como el correo electrónico, los medios sociales y la nube pública, que están fuera del control de la empresa. Por ejemplo, un empleado envía las imágenes de ingeniería más recientes desde una cuenta de correo electrónico personal, copia y pega la información del producto en un tweet o guarda un informe de ventas en curso en un almacenamiento en la nube pública.

**Windows Information Protection** ayuda a proporcionar protección ante esta pérdida potencial de datos sin interferir como contrapartida en la experiencia de empleado. También ayuda a proteger los datos y aplicaciones empresariales ante las pérdidas de datos accidentales en dispositivos propiedad de la empresa y personales que los empleados llevan al trabajo sin necesidad de realizar cambios en su entorno u otras aplicaciones.

Esta directiva de Intune administra la lista de aplicaciones protegidas por Windows Information Protection, las ubicaciones de red de la empresa, el nivel de protección y la configuración de cifrado.

>[!NOTE]
> Para usar la aplicación Portal de empresa de Windows 10 con Windows Information Protection, debe agregar la aplicación Portal de empresa en el modo **Exento** de Windows Information Protection. 

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información, vea:
-  [Protege los datos de tu empresa con Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
- [Crear una directiva de Windows Information Protection (WIP) con Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune)
- [Crear una directiva Windows Information Protection (WIP) con MDM usando el portal de Azure de Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune-azure)
- [Crear una directiva Windows Information Protection (WIP) con MAM usando el portal de Azure de Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure)
