---
ms.openlocfilehash: 8483ed3d4198e228bdaaf4723b2c9c0dca9cecfc
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830507"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisitos de credenciales de Azure AD e Intune

La autenticación y la autorización se basan en las credenciales de Azure AD y en el control de acceso basado en roles (RBAC) de Intune. Todos los administradores globales y los administradores de servicios de Intune del inquilino tienen acceso al Almacén de datos de forma predeterminada. Use roles de Intune para proporcionar acceso a más usuarios. Para ello, concédales acceso al recurso **Almacenamiento de datos de Intune**.

Los requisitos para acceder al Almacén de datos de Intune (incluida la API) son:

- El usuario debe ser uno de los siguientes:
  - Un administrador global de Azure AD.
  - Un administrador del servicio de Intune.
  - Usuario con acceso basado en roles al recurso **Almacenamiento de datos de Intune**.
  - Autenticación sin usuario mediante [autenticación de solo aplicación](../developer/data-warehouse-app-only-auth.md). 
