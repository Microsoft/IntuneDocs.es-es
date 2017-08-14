---
title: "Punto de conexión de la API de Almacenamiento de datos de Intune | Microsoft Docs"
description: "En este tema de referencia se describe la estructura de la dirección URL de la API."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7723bb42eedcd97142f039ca52b60911fa91838b
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2017
---
# <a name="intune-data-warehouse-api-endpoint"></a>Punto de conexión de la API de Almacenamiento de datos de Intune

Puede usar la API de Almacenamiento de datos de Intune con una cuenta con controles de acceso basados en roles específicos y credenciales de Azure AD. Después, autorizará al cliente REST con Azure AD mediante OAuth 2.0 y, por último, formará una dirección URL significativa para llamar a un recurso de almacenamiento de datos.

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisitos de credenciales de Azure AD e Intune

La autenticación y la autorización se basan en las credenciales de Azure AD y en el control de acceso basado en roles (RBAC) de Intune. Todos los administradores globales y los administradores de servicios de Intune del inquilino tienen acceso a la API de forma predeterminada. Use los roles de Intune para proporcionar acceso a más usuarios. Para ello, concédales acceso al **recurso de informes**.

Los requisitos para tener acceso a la API son los siguientes:

  -  El usuario debe tener asignada una licencia de Intune.
  -  El usuario debe ser uno de los siguientes:
      -  Un administrador global de Azure AD.
      -  Un administrador del servicio de Intune.
      -  Un usuario con acceso basado en roles al recurso de **informes**.

## <a name="authorization"></a>Autorización

Azure Active Directory (Azure AD) usa OAuth 2.0 para permitir autorizar el acceso a aplicaciones web y API web en el inquilino de Azure AD. En esta guía independiente del idioma se describe cómo enviar y recibir mensajes HTTP sin usar ninguna de nuestras bibliotecas de código abierto. El flujo del código de autorización de OAuth 2.0 se describe en la [sección 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) de la especificación de OAuth 2.0.

Para obtener más información, vea [Autorización del acceso a aplicaciones web mediante OAuth 2.0 y Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>Estructura de la dirección URL de la API

Los puntos de conexión de la API de Almacenamiento de datos leen las entidades de cada conjunto. La API admite un verbo HTTP **GET** y un subconjunto de opciones de consulta.

La dirección URL de Intune usa el formato siguiente:  
https://fef.{***location***}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{***entity-collection***}?api-version={***api-version***}

La dirección URL contiene los elementos siguientes:

| Elemento | Ejemplo | Descripción |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| ubicación | msua06 | Para localizar la URL base, vea la hoja de la API de Almacenamiento de datos en Azure Portal. |
| entity-collection | fechas | Nombre de la colección de entidades OData. Para obtener más información sobre las colecciones y las entidades del modelo de datos, vea [Data Model](reports-ref-data-model.md) (Modelo de datos). |
| api-version | beta | "Version" hace referencia a la versión de la API a la que se va a tener acceso. Para obtener más información, vea [Version](#API-version-information) (Versión). |


## <a name="api-version-information"></a>Información de versión de la API

La versión actual de la API es `beta`. 

## <a name="odata-query-options"></a>Opciones de consulta OData

La versión actual admite los siguientes parámetros de consulta OData: `$skip, $top, $filter, $orderby`.