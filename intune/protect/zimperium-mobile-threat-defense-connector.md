---
title: Conector MTD de Zimperium con Intune
titleSuffix: Intune on Azure
description: Obtenga información sobre cómo integrar Intune con Zimperium Mobile Threat Defense para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 33d4039e430699c5b8e15c1f9b817d8e2a25d029
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728070"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Conector Mobile Threat Defense de Zimperium con Intune

Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Zimperium, una solución de defensa contra amenazas móviles (MTD) integrada en Microsoft Intune. El riesgo se evalúa en función de la telemetría recopilada de los dispositivos que ejecutan la aplicación Zimperium.

Puede configurar directivas de acceso condicional basadas en la evaluación de riesgos de Zimperium habilitada mediante las directivas de cumplimiento de dispositivos de Intune. La directiva de evaluación de riesgos puede permitir o bloquear el acceso de dispositivos no compatibles a recursos corporativos en función de las amenazas detectadas.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>¿Cómo ayudan Intune y Zimperium a proteger los recursos de la empresa?

La aplicación Zimperium para iOS y Android capta el sistema de archivos, la pila de red, el dispositivo y la telemetría de aplicaciones cuando está disponible. Después, envía los datos de telemetría al servicio en la nube de Zimperium para evaluar el riesgo del dispositivo frente a las amenazas móviles.

La directiva de cumplimiento de dispositivos de Intune incluye una regla para Mobile Threat Defense de Zimperium que se basa en la evaluación del riesgo de Zimperium. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó. Si se detecta que el dispositivo no cumple con la directiva, se bloqueará el acceso de los usuarios a los recursos corporativos, como Exchange Online y SharePoint Online. Los usuarios también reciben los pasos de la aplicación Zimperium instalada en sus dispositivos para resolver el problema y volver a obtener acceso a los recursos corporativos.

## <a name="sample-scenarios"></a>Escenarios de ejemplo

Vea a continuación algunos escenarios de integración de Zimperium con Intune:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Control del acceso basado en amenazas de aplicaciones malintencionadas

Cuando se detectan aplicaciones malintencionadas, como malware, en los dispositivos, puede bloquearlos de la siguiente manera hasta que la amenaza se resuelva:

- Conectarse al correo electrónico corporativo

- Sincronizar los archivos corporativos mediante la aplicación OneDrive para el trabajo

- Acceder a las aplicaciones de empresa

**Bloquear cuando se detectan aplicaciones malintencionadas:**

![Imagen conceptual de aplicaciones malintencionadas detectadas](./media/zimperium-mobile-threat-defense-connector/Maliciousapps_blocked_Zimperium.png)

**Acceso concedido tras la corrección:**

![Imagen conceptual de acceso concedido tras la corrección](./media/zimperium-mobile-threat-defense-connector/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>Control del acceso basado en amenazas a la red

Detecte amenazas para la red, como **ataques de tipo Man-in-the-middle**, y proteja el acceso a las redes Wi-Fi según el riesgo del dispositivo.

**Bloquear el acceso de red a través de Wi-Fi:**

![Bloquear el acceso de red a través de Wi-Fi](./media/zimperium-mobile-threat-defense-connector/network_wifi_blocked_Zimperium.png)

**Acceso concedido tras la corrección:**

![Acceso concedido tras la solución](./media/zimperium-mobile-threat-defense-connector/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Control del acceso a SharePoint Online basado en amenazas a la red

Detecte amenazas para la red, como **ataques de tipo Man-in-the-middle**, y evite la sincronización de archivos corporativos según el riesgo del dispositivo.

**Bloqueo de SharePoint Online cuando se detectan amenazas a la red:**

![Bloqueo de SharePoint Online cuando se detectan amenazas a la red](./media/zimperium-mobile-threat-defense-connector/network_spo_blocked_Zimperium.png)

**Acceso concedido tras la corrección:**

![Acceso concedido tras la solución](./media/zimperium-mobile-threat-defense-connector/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>Plataformas compatibles

- **Android 4.1 y versiones posteriores**

- **iOS 8 y versiones posteriores**

## <a name="prerequisites"></a>Requisitos previos

- Azure Active Directory Premium

- Suscripción a Microsoft Intune

- Suscripción a Mobile Threat Defense de Zimperium

  - Para más información, consulte el [sitio web de Zimperium](https://www.zimperium.com/zips-mobile-ips).

## <a name="next-steps"></a>Pasos siguientes

- [Integrar Zimperium con Intune](zimperium-mtd-connector-integration.md)

- [Configurar aplicaciones Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Crear una directiva de cumplimiento de dispositivos de Zimperium](mtd-device-compliance-policy-create.md)

- [Habilitar el conector MTD de Zimperium](mtd-connector-enable.md)
