---
title: Bloquear dispositivos con Microsoft Intune - Azure | Microsoft Docs
description: Use la acción de bloqueo remoto de Microsoft Intune para bloquear un dispositivo protegido por un PIN o contraseña.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 328f196a61f26fa787495e515fb5de3e0d32f7b2
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231288"
---
# <a name="remotely-lock-devices-with-intune"></a>Bloqueo remoto de dispositivos con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Bloqueo remoto** bloquea el dispositivo. Para desbloquear el dispositivo, el propietario debe introducir su código de acceso. Puede bloquear de forma remota los dispositivos que dispongan de PIN o contraseña. Los dispositivos que no tienen PIN o contraseña no se pueden bloquear de forma remota.

## <a name="supported-platforms"></a>Plataformas compatibles

**Bloqueo remoto** es compatible con las siguientes plataformas:

- Android
- Dispositivos de quiosco de Android Enterprise
- Dispositivos de perfil de trabajo de Android Enterprise
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 y versiones posteriores

**Bloqueo remoto** no es compatible con:
- Windows 10 Escritorio

> [!NOTE]
> Para los dispositivos MacOS, establezca un PIN de recuperación de 6 dígitos. Una vez bloqueado el dispositivo, en **Información general del dispositivo** se muestra el PIN hasta que se envía otra acción de dispositivo.

## <a name="remote-lock-a-device"></a>Bloquear de forma remota un dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** > **Todos los dispositivos**.
4. En la lista de dispositivos, seleccione un dispositivo y, luego, seleccione la acción **Bloqueo remoto**.

## <a name="next-steps"></a>Pasos siguientes

- Para ver el estado de esta acción, seleccione **Microsoft Intune** > **Dispositivos** > **Acciones de dispositivo**. 
- Consulte [Acciones disponibles](device-management.md) para ver más acciones para administrar los dispositivos.
