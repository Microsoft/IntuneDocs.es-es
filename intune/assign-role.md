---
title: Asignación de un rol a un usuario de Intune
description: Obtenga información sobre cómo asignar un rol integrado o personalizado a un usuario de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a59c413fcc11dfce76152a7325517703a71785d2
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508193"
---
# <a name="assign-a-role-to-an-intune-user"></a>Asignación de un rol a un usuario de Intune

Puede asignar un rol [integrado](role-based-access-control.md#built-in-roles) o [personalizado](create-custom-role.md) a un usuario de Intune.

Para crear, editar o asignar roles, la cuenta debe tener uno de los siguientes permisos en Azure AD:
- **Administrador global**
- **Administrador del servicio de Intune**

Para obtener una lista completa de los permisos de cada rol integrado, vea la [tabla de RBAC de Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a).

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.

3. En la hoja **Intune**, seleccione **Roles** > **Todos los roles**.

4. En la hoja **Roles de Intune: Todos los roles**, elija el rol integrado que quiera asignar.

5. En la hoja <*nombre del rol*> - **Información general**, elija **Administrar** > **Asignaciones**.

6. En la hoja de roles personalizados, elija **Asignar**.

7. En la hoja **Asignaciones de roles**, escriba un **nombre de asignación** y una **descripción** opcional para la asignación.

8. En **Miembros (grupos)**, elija un grupo que contenga el usuario al que quiere conceder los permisos.

9. En **Ámbito (grupos)**, elija un grupo que contenga los usuarios o los dispositivos que el miembro anterior tendrá permiso para administrar.

10. En **Ámbito (etiquetas)**, elija las etiquetas donde se aplicará esta asignación de roles.

11. Cuando haya terminado, seleccione **Aceptar**. La nueva asignación se muestra en la lista de asignaciones.


## <a name="next-steps"></a>Pasos siguientes
- [Más información sobre el control de acceso basado en rol en Intune](role-based-access-control.md)
- [Creación de un rol personalizado](create-custom-role.md)