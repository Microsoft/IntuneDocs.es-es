---
title: Inscripción de dispositivos mediante una cuenta de administrador de inscripción de dispositivos
titleSuffix: Microsoft Intune
description: Use la cuenta del administrador de inscripciones de dispositivos para inscribir dispositivos en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8bbb1c7ec7151a09c8eeae33f4252781e5338f7
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048325"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>Inscripción de dispositivos en Intune mediante una cuenta de administrador de inscripción de dispositivos

Puede inscribir hasta 1000 dispositivos móviles con una sola cuenta de Azure Active Directory mediante una cuenta de administrador de inscripción de dispositivos (DEM). DEM es un permiso de Intune que puede aplicarse a una cuenta de usuario de AAD y que permite al usuario inscribir hasta 1000 dispositivos. Una cuenta de DEM es útil en escenarios donde los dispositivos están inscritos y preparados antes de entregarlos a los usuarios de los dispositivos.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitaciones de los dispositivos que están inscritos con una cuenta DEM

Los dispositivos y las cuentas de los usuarios de DEM inscritos con una cuenta de usuario de DEM tienen las siguientes limitaciones:

  - Se debe asignar una cuenta de usuario DEM a una licencia de Intune.
  - No se puede realizar el borrado desde el Portal de empresa. Se puede borrar un dispositivo inscrito por una cuenta de usuario de DEM desde Intune en Azure Portal.
  - Solo el dispositivo local aparece en el sitio web o en la aplicación de Portal de empresa.
  - Las cuentas de usuario de DEM no pueden usar aplicaciones del Programa de Compras por Volumen de Apple (VPP) con las licencias de usuario de Apple VPP debido a los requisitos de ID de Apple por usuario para la administración de aplicaciones.
  - Los dispositivos pueden instalar aplicaciones de VPP si disponen de licencias de dispositivo de Apple VPP.
  - Los dispositivos están bloqueados para el acceso condicional con la excepción de Windows 10 1803+.
  - Todos los dispositivos inscritos con cuentas DEM deben tener la licencia correspondiente para que Intune los administre. La licencia puede ser una licencia de usuario de Intune o una licencia de dispositivo de Intune.



## <a name="add-a-device-enrollment-manager"></a>Agregar un administrador de inscripción de dispositivos

1.  En Intune, en [Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Administradores de inscripción de dispositivos**.

2.  Seleccione **Agregar**.

3.  En la hoja **Agregar usuario**, escriba un nombre principal de usuario para el usuario de DEM y seleccione **Agregar**. El usuario DEM se agrega a la lista de usuarios DEM.

## <a name="permissions-for-dem"></a>Permisos para DEM

Se requieren los roles de administrador global o administrador de servicios de Intune de Azure AD para:
- Asignar permisos de DEM a una cuenta de usuario de Azure AD.
- Ver todos los usuarios de DEM.

Si un usuario no tiene asignado el rol de administrador global o de administrador de servicios de Intune, pero tiene habilitados permisos de lectura para el rol de administradores de inscripción de dispositivos que tiene asignado, solo podrá ver los usuarios de DEM que haya creado.


## <a name="remove-device-enrollment-manager-permissions"></a>Eliminación de los permisos de administrador de inscripción de dispositivos

La eliminación de un administrador de inscripción de dispositivos no afecta a los dispositivos inscritos.

**Eliminación de un administrador de inscripción de dispositivos**

1. En [Intune, en Azure Portal](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** y, luego, **Administradores de inscripción de dispositivos**.
2. En la hoja **Administradores de inscripción de dispositivos**, seleccione el usuario DEM y **Eliminar**.

