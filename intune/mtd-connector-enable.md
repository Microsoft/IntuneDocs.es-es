---
title: Habilitar el conector Mobile Threat Defense con Intune
titleSuffix: Intune on Azure
description: Habilite el conector Mobile Threat Defense en Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a5dfef35c9f2d2fa543d8b19c2566b25d47b8f72
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2017
---
# <a name="enable-mobile-threat-defense-in-intune"></a>Habilitar Mobile Threat Defense en Intune

> [!NOTE] 
> La información de este tema se aplica a todos los asociados de Mobile Threat Defense.

Para habilitar la conexión de Mobile Threat Defense (MTD) en Intune, ya debe haber configurado el conector de Intune en la consola de solución de MTD.

## <a name="to-enable-the-mtd-connector"></a>Para habilitar el conector de MTD

1. Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de Intune. Después de iniciar sesión correctamente, verá el **Panel de Azure**.

2. En el **panel de Azure**, elija **Más servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Pulse **Intune** y se abrirá el **panel de Intune**.

4. En el **panel de Intune**, elija **Cumplimiento de dispositivos** y, luego, elija **Mobile Threat Defense** en la sección **Configuración**.

5. En la hoja **Mobile Threat Defense**, elija **Agregar**.

6. Seleccione su solución de MTD como el **conector para Mobile Threat Defense a configurar** en la lista desplegable.

    ![Configuración de MTD en Azure Portal de Intune](./media/enable-mtd-connector-1.png)

7. Habilite las opciones de alternancia según los requisitos de su organización.

## <a name="mtd-toggle-options"></a>Opciones de alternancia de MTD

Puede decidir qué opciones de alternancia de MTD necesita habilitar según los requisitos de su organización. A continuación se muestran más detalles:

- **Connect Android 4.1+ devices to [MTD partner name] for Work MTD** (Conectar dispositivos Android 4.1+ con MTD de [nombre del partner de MTD] for Work): cuando habilita esta opción, puede hacer que los dispositivos Android 4.1+ informen un riesgo de seguridad a Intune.
    - **Mark as non-compliant if no data is received** (Marcar como no conforme si no se reciben datos): si Intune no recibe datos sobre un dispositivo en esta plataforma por parte del asociado de MTD, considere que el dispositivo como no conforme.
<br></br>
- **Connect iOS 8.0+ devices to [MTD partner name] for Work MTD** (Conectar dispositivos iOS 8.0+ con MTD de [nombre del partner de MTD] for Work): cuando habilita esta opción, puede hacer que los dispositivos Android 4.1+ informen un riesgo de seguridad a Intune.
    - **Mark as non-compliant if no data is received** (Marcar como no conforme si no se reciben datos): si Intune no recibe datos sobre un dispositivo en esta plataforma por parte del asociado de MTD, considere que el dispositivo como no conforme.
<br></br>
- **Block unsupported OS versions** (Bloquear versiones de SO no compatibles): bloquee si el dispositivo ejecuta un sistema operativo inferior a la versión mínima compatible.

- **Number of days until partner is unresponsive** (Número de días hasta que el asociado no responda): número de días de inactividad antes de que Intune considere que el asociado no responde porque se perdió la conexión. Intune omite el estado de cumplimiento de los asociados de MTD que no responden.

> [!IMPORTANT] 
> Debe agregar y asignar las aplicaciones de MTD antes de crear el cumplimiento de dispositivo y las reglas de directiva de acceso condicional. Esto garantiza que la aplicación de MTD esté lista y disponible para que los usuarios finales la instalen antes de poder acceder al correo electrónico u otros recursos de empresa.

> [!TIP]
> Puede ver el **estado de conexión** y la hora de **última sincronización** entre Intune y el asociado de MTD en la hoja Mobile Threat Defense.

## <a name="next-steps"></a>Pasos siguientes

[Creación de directiva de cumplimiento de dispositivos de Mobile Threat Defense con Intune](mtd-device-compliance-policy-create.md)