---
title: Asignación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Use Azure Portal para asignar perfiles de dispositivo y directivas a los usuarios y a los dispositivos. Aprenda a excluir grupos de una asignación de perfil en Microsoft InTune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8263bc7a6a38431d942bd8714b1911a94cb4a24a
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57239023"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Asignación de perfiles de dispositivo en Microsoft Intune

Después de crear un perfil, puede asignarlo a grupos de Azure Active Directory (Azure AD).

## <a name="assign-a-device-profile"></a>Asignar un perfil de dispositivo

1. En [Azure Portal](https://portal.azure.com), seleccione **All services** (Todos los servicios) y busque **Microsoft Intune**.
2. En **Microsoft Intune**, seleccione **Configuración del dispositivo** y **Perfiles**.
3. En la lista de perfiles, seleccione el que quiera asignar y, luego, **Asignaciones**.
4. Elija **Incluir** para incluir grupos o **Excluir** para excluir grupos y, después, seleccione los grupos.  

    ![Captura de pantalla de las opciones para incluir o excluir grupos de una asignación de perfil](./media/group-include-exclude.png)

5. Al seleccionar los grupos, se elige un grupo de Azure AD. Para seleccionar varios grupos, mantenga presionada la tecla **Ctrl**.
6. Cuando haya terminado, seleccione **Guardar**.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de una asignación de perfil

Los perfiles de configuración de dispositivo de Intune permiten excluir grupos de una asignación de directiva. Por ejemplo, puede asignar un perfil de dispositivo al grupo **Todos los usuarios corporativos**, pero excluir a todos los miembros del grupo **Personal de administración sénior**.

Al excluir grupos de una asignación, se excluyen solo los usuarios, o solo grupos de dispositivos (no una combinación de grupos), ya que Intune no considera ninguna relación de usuario a dispositivo. Es posible que la inclusión de grupos de usuarios a la vez que se excluyen grupos de dispositivos no genere los resultados que espera. Si se usan grupos mixtos o hay otros conflictos, la inclusión tiene prioridad sobre la exclusión.

Por ejemplo, quiere asignar un perfil de dispositivo a todos los dispositivos de la organización, excepto los de pantalla completa. Incluye el grupo **Todos los usuarios**, pero excluye al grupo **Todos los dispositivos**. En este caso, todos los usuarios y sus dispositivos obtienen la directiva, aunque el dispositivo del usuario forme parte del grupo **Todos los dispositivos**.

La exclusión solo busca los miembros directos de los grupos y no incluye los dispositivos que están asociados a un usuario. En cambio, los dispositivos que no tienen un usuario no obtienen la directiva. Esto ocurre porque esos dispositivos no tienen ninguna relación con el grupo **Todos los usuarios**.

Si incluye **Todos los dispositivos** y excluye **Todos los usuarios**, todos los dispositivos reciben la directiva. En este escenario, la intención es excluir aquellos dispositivos que tienen un usuario asociado de esta directiva. En cambio, no se excluyen los dispositivos porque la exclusión solo compara miembros de grupo directos.

## <a name="next-steps"></a>Pasos siguientes
Consulte [Cómo supervisar perfiles de dispositivo](device-profile-monitor.md) para obtener instrucciones a fin de supervisar las asignaciones de perfil de dispositivo.
