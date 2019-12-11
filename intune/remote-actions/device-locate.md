---
title: Búsqueda de dispositivos iOS perdidos con Microsoft Intune - Azure | Microsoft Docs
description: Busque dispositivos iOS perdidos o robados mediante la característica de búsqueda de dispositivos de Microsoft Intune. Puede obtener detalles sobre la información de privacidad y seguridad usando la acción de búsqueda de dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 817f46558932c074abc37b45d2885496419a0db0
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712420"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Búsqueda de dispositivos iOS perdidos o robados con Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Para descubrir la ubicación de un dispositivo iOS robado o perdido en un mapa, use la acción **Buscar dispositivo**. El dispositivo debe estar en modo supervisado. Antes de realizar esta acción, asegúrese de que el dispositivo esté en [modo perdido](device-lost-mode.md).

## <a name="supported-platforms"></a>Plataformas compatibles

- iOS 9.3 y versiones posteriores

Esta característica no se admite en los siguientes sistemas: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Búsqueda de un dispositivo perdido o robado

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, seleccione un dispositivo iOS y seleccione **...Más**. Luego, elija la acción remota **Buscar dispositivo**.
5. Al encontrar el dispositivo, su ubicación se mostrará en **Buscar dispositivo**.
    ![Captura de pantalla de Buscar dispositivo con Intune en Azure](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Activación de la alerta sonora de modo perdido en un dispositivo iOS

Si alguien ha perdido su dispositivo iOS 9.3 o posterior, puede desencadenar de forma remota una alerta sonora en el dispositivo para que el usuario pueda encontrarlo. El dispositivo debe estar en [modo perdido](device-lost-mode.md).

En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Dispositivos** > **Todos los dispositivos** > seleccione un dispositivo iOS > **Información general** > **Más** > **Play Lost mode sound (supervise only)** (Reproducir sonido de modo perdido [solo supervisar]).

El sonido sigue reproduciéndose hasta que el usuario lo deshabilita en el dispositivo o este se quita del modo perdido.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Información de seguridad y privacidad de las acciones de modo perdido y buscar dispositivo
- No se envía ningún dato relacionado con la ubicación del dispositivo a Intune hasta que active esta acción.
- Cuando se usa la acción Buscar dispositivo, las coordenadas de latitud y longitud del dispositivo se puede recuperar mediante Graph API.
- Los datos se almacenan durante 24 horas y, más adelante, se eliminan. No se puede quitar manualmente la información de ubicación.
- Los datos de ubicación permanecen cifrados mientras están almacenados y transmitiéndose.
- Al configurar el modo perdido, puede personalizar un mensaje para que se muestre en la pantalla de bloqueo. Para ayudar a la persona que encuentre el dispositivo, incluya en este mensaje detalles específicos para devolver el dispositivo perdido.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de habilitación de Buscar dispositivo, abra **Dispositivos** y seleccione **Acciones de dispositivo**.
