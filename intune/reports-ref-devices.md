---
title: Dispositivos - Almacenamiento de datos de Intune
titlesuffix: Microsoft Intune
description: Tema de referencia sobre la categoría Dispositivos de las colecciones de entidades de la API de Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe16111095051c1fddb4b87d5b4f815ae2798e92
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566376"
---
# <a name="reference-for-devices-entities"></a>Referencia de las entidades Devices

La categoría **Dispositivos** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la siguiente:

  -  Tipo de dispositivo
  -  Estado de registro e inscripción del dispositivo
  -  Propiedad del dispositivo
  -  Estado de administración del dispositivo
  -  Estado de pertenencia del dispositivo en Azure AD
  -  Estado de inscripción
  -  Información histórica sobre el dispositivo
  -  Inventario de aplicaciones del dispositivo

## <a name="devicetypes"></a>DeviceTypes

La entidad **DeviceTypes** representa el tipo de dispositivo al que hacen referencia otras entidades de almacenamiento de datos. Normalmente, el tipo de dispositivo describe el modelo del dispositivo, el fabricante o una combinación de ambos.

| Propiedad  | Descripción |
|---------|------------|
| DeviceTypeID |Identificador único del tipo de dispositivo. |
| DeviceTypeKey |Identificador único del tipo de dispositivo en el almacenamiento de datos. Clave suplente. |
| DeviceTypeName |Tipo de dispositivo |

### <a name="example"></a>Ejemplo

| deviceTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Escritorio |Dispositivo de escritorio de Windows |
| 1 |WindowsRT |Dispositivo WindowsRT |
| 2 |WinMO6 |Dispositivo Windows Mobile 6.0 |
| 3 |Nokia |Dispositivo Nokia |
| 4 |WindowsPhone |Dispositivo Windows Phone |
| 5 |Mac |Dispositivo Mac |
| 6 |WinCE |Dispositivo Windows CE |
| 7 |WinEmbedded |Dispositivo Windows Embedded |
| 8 |IPhone |Dispositivo iPhone |
| 9 |IPad |Dispositivo iPad |
| 10 |IPod |Dispositivo iPod |
| 11 |Android |Dispositivo Android administrado mediante el Administrador de dispositivos |
| 12 |ISocConsumer |Dispositivo iSoc Consumer |
| 14 |MacMDM |Dispositivo Mac OS X administrado con el agente MDM integrado |
| 15 |HoloLens |Dispositivo HoloLens |
| 16 |SurfaceHub |Dispositivo Surface Hub |
| 17 |AndroidForWork |Dispositivo Android administrado mediante el propietario con perfil Android |
| 100 |BlackBerry |Dispositivo BlackBerry |
| 101 |Palm |Dispositivo Palm |
| 255 |Unknown |Tipo de dispositivo desconocido |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

La entidad **ClientRegistrationStateTypes** representa el tipo de registro al que hacen referencia otras tablas de almacenamiento de datos.

| Propiedad  | Descripción |
|---------|------------|
| clientRegisterationStateID |Identificador único del estado de registro. |
| clientRegisterationStateKey |Identificador único del estado de registro en el almacenamiento de datos. Clave suplente. |
| clientRegisterationStateName |Estado de registro. |

### <a name="example"></a>Ejemplo

| ClientRegisterationStateID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |NotRegistered |No registrado. |
| 1 |SMSIDConflict |Conflicto de identificador de SMS. |
| 2 |Registrado |Registrado |
| 3 |Revoked |El estado significa que el administrador de TI ha bloqueado al cliente y el cliente se puede desbloquear. Un dispositivo también puede encontrarse en estado Revoked después de que se haya borrado o retirado. |
| 4 |KeyConflict |Conflicto de clave. |
| 5 |ApprovalPending |Pendiente de aprobación. |
| 6 |ResetCert |Certificado establecido. |
| 7 |NotRegisteredPendingEnrollment |No registrado y pendiente de inscripción. |
| 8 |Unknown |Estado desconocido. |

## <a name="enrollmentactivities"></a>enrollmentActivities 
La entidad **EnrollmentActivity** indica la actividad de una inscripción de dispositivos.

| Propiedad                      | Descripción                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Clave de la fecha en la que se ha registrado esta actividad de inscripción.               |
| deviceEnrollmentTypeKey       | Clave del tipo de inscripción.                                        |
| deviceTypeKey                 | Clave del tipo de dispositivo.                                                |
| enrollmentEventStatusKey      | Clave del estado que indica si la inscripción se ha realizado correctamente o si se ha producido un error.    |
| enrollmentFailureCategoryKey  | Clave de la categoría del error de la inscripción (si se ha producido un error en la inscripción).        |
| enrollmentFailureReasonKey    | Clave del motivo del error de la inscripción (si se ha producido un error en la inscripción).          |
| osVersion                     | Versión del sistema operativo del dispositivo.                               |
| count                         | Recuento total de las actividades de inscripción que coinciden con las clasificaciones anteriores.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
La entidad **EnrollmentEventStatus** indica el resultado de una inscripción de dispositivos.

| Propiedad                   | Descripción                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | Identificador único del estado de la inscripción en el almacenamiento de datos (clave suplente).  |
| enrollmentEventStatusName  | Nombre del estado de la inscripción. Vea los ejemplos siguientes.                            |

### <a name="example"></a>Ejemplo

| enrollmentEventStatusName  | Descripción                            |
|----------------------------|----------------------------------------|
| Correcto                    | Inscripción de dispositivo correcta.         |
| Failed                     | Inscripción de dispositivo errónea.             |
| No disponible              | El estado de la inscripción no está disponible.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
La entidad **EnrollmentFailureCategory** indica el motivo del error de una inscripción de dispositivos. 

| Propiedad                       | Descripción                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | Identificador único de la categoría del error de la inscripción en el almacenamiento de datos (clave suplente).  |
| enrollmentFailureCategoryName  | Nombre de la categoría del error de la inscripción. Vea los ejemplos siguientes.                            |

### <a name="example"></a>Ejemplo

| enrollmentFailureCategoryName   | Descripción                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| No aplicable                  | La categoría del error de la inscripción no es aplicable.                                                            |
| No disponible                   | La categoría del error de la inscripción no está disponible.                                                             |
| Unknown                         | Error desconocido.                                                                                                |
| Autenticación                  | Error de autenticación.                                                                                        |
| Autorización                   | La llamada se ha autenticado, pero no tiene autorización para inscribirse.                                                         |
| AccountValidation               | Error al validar la cuenta para la inscripción. (Cuenta bloqueada, inscripción no habilitada).                      |
| UserValidation                  | No se ha podido validar al usuario. (El usuario no existe, falta la licencia).                                           |
| DeviceNotSupported              | El dispositivo no es compatible con la administración de dispositivos móviles.                                                         |
| InMaintenance                   | La cuenta está en mantenimiento.                                                                                    |
| BadRequest                      | El cliente ha enviado una solicitud que el servicio no entiende o no admite.                                        |
| FeatureNotSupported             | Las características que usa esta inscripción no se admiten en esta cuenta.                                        |
| EnrollmentRestrictionsEnforced  | Las restricciones de inscripción que ha configurado el administrador han bloqueado esta inscripción.                                          |
| ClientDisconnected              | El cliente ha agotado el tiempo de espera o el usuario final ha anulado la inscripción.                                                        |
| UserAbandonment                 | El usuario final ha anulado la inscripción. (El usuario final ha iniciado la inscripción, pero no se ha completado de manera oportuna).  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
La entidad **EnrollmentFailureReason** indica un motivo más detallado para el error de inscripción de un dispositivo dentro de una categoría de error determinada.  

| Propiedad                     | Descripción                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | Identificador único del motivo del error de la inscripción en el almacenamiento de datos (clave suplente).  |
| enrollmentFailureReasonName  | Nombre del motivo del error de la inscripción. Vea los ejemplos siguientes.                            |

### <a name="example"></a>Ejemplo

| enrollmentFailureReasonName      | Descripción                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| No aplicable                   | El motivo del error de la inscripción no es aplicable.                                                                                                                                                       |
| No disponible                    | El motivo del error de la inscripción no está disponible.                                                                                                                                                        |
| Unknown                          | Error desconocido.                                                                                                                                                                                         |
| UserNotLicensed                  | No se ha encontrado al usuario en Intune o no tiene una licencia válida.                                                                                                                                     |
| UserUnknown                      | No se conoce al usuario en Intune.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Solo un usuario puede inscribir un dispositivo. Otro usuario ha inscrito este dispositivo anteriormente.                                                                                                                |
| EnrollmentOnboardingIssue        | La entidad de administración de dispositivos móviles (MDM) de Intune aún no se ha configurado.                                                                                                                                 |
| AppleChallengeIssue              | La instalación del perfil de administración de iOS se ha retrasado o se ha producido un error.                                                                                                                                         |
| AppleOnboardingIssue             | Se necesita un certificado push MDM de Apple para inscribir en Intune.                                                                                                                                       |
| DeviceCap                        | El usuario ha intentado inscribir más dispositivos que el máximo permitido.                                                                                                                                        |
| AuthenticationRequirementNotMet  | El servicio de inscripción de Intune no pudo autorizar esta solicitud.                                                                                                                                            |
| UnsupportedDeviceType            | El dispositivo no cumple los requisitos mínimos para la inscripción en Intune.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | No se pudo inscribir este dispositivo debido a una regla de restricción de inscripción configurada.                                                                                                                          |
| BulkDeviceNotPreregistered       | No se han encontrado el identificador de equipo móvil internacional (IMEI) o el número de serie del dispositivo.  Sin este identificador, los dispositivos se reconocen como dispositivos personales que están bloqueados.  |
| FeatureNotSupported              | El usuario ha intentado acceder a una característica que todavía no está disponible para todos los clientes o no es compatible con la configuración de Intune.                                                            |
| UserAbandonment                  | El usuario final ha anulado la inscripción. (El usuario final ha iniciado la inscripción, pero no se ha completado de manera oportuna).                                                                                           |
| APNSCertificateExpired           | No se pueden administrar dispositivos de Apple con un certificado push MDM de Apple expirado.                                                                                                                            |

## <a name="enrollmenttypes"></a>EnrollmentTypes

La entidad **EnrollmentTypes** indica cómo se ha inscrito un dispositivo. El tipo de inscripción captura el método de inscripción. En los ejemplos se muestran los diferentes tipos de inscripción y su significado.

| Propiedad  | Descripción |
|---------|------------|
| managementStateID |Identificador único del estado de administración. |
| managementStateKey |Identificador único del estado de administración en el almacenamiento de datos. Clave suplente. |
| managementStateName |Indica el estado de la acción remota aplicada a este dispositivo. |

### <a name="example"></a>Ejemplo

| enrollmentTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Unknown |No se recopiló el tipo de inscripción |
| 1 |UserEnrollment |Inscripción iniciada por el usuario. |
| 2 |DeviceEnrollment |Inscripción del dispositivo mediante un perfil sin usuario. |
| 3 |DeviceEnrollmentWithUDA |Inscripción del dispositivo mediante un perfil UDA. |
| 4 |AzureDomainJoined |Inscripción del dispositivo iniciada por el usuario mediante Azure Active Directory. |
| 5 |UserEnrollmentWithServiceAccount |Inscripción iniciada por el usuario mediante una cuenta de servicio. |
| 6 |DepDeviceEnrollment |Inscripción de dispositivo DEP mediante un perfil sin usuario. |
| 7 |DepDeviceEnrollmentWithUDA |Inscripción de dispositivo DEP mediante un perfil UDA. |
| 8 |AutoEnrollment |Inscripción combinada de DRS y MDM para escenario BYOD. |

## <a name="ownertypes"></a>OwnerTypes

La entidad **EnrollmentTypes** indica si el dispositivo es corporativo, personal o desconocido.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| ownerTypeID |Identificador único del tipo de propietario. | |
| ownerTypeKey |Identificador único del tipo de propietario en el almacenamiento de datos. Clave suplente. | |
| ownerTypeName |Representa el tipo de propietario de los dispositivos:  <br>Corporativo: dispositivo es propiedad de la empresa. <br>Personal: el dispositivo es de propiedad personal (BYOD).  <br>Desconocido: no hay información sobre este dispositivo. |Empresa Personal desconocido |

> [!Note]  
> Para el `ownerTypeName` en Azure AD al crear grupos dinámicos para los dispositivos, deberá establecer el valor de filtro `deviceOwnership` como `Company`. Para obtener más información, consulte [reglas para dispositivos](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="mdmstatuses"></a>MdmStatuses

La entidad **MdmStatuses** indica el estado de cumplimiento del dispositivo.

| Propiedad  | Descripción |
|---------|------------|
| MdmStatusID |Identificador único del estado de cumplimiento. |
| MdmStatusKey |Identificador único del estado de cumplimiento en el almacenamiento de datos. Clave suplente. | 
| ComplianceStatus |Estado de cumplimiento del dispositivo. Debe tener uno de los valores de la tabla siguiente. | 


### <a name="example"></a>Ejemplo

| MdmStatusID  | ComplianceStatus | Descripción |
|---------|------------|--------|
| 0 |Unknown |El estado de cumplimiento del dispositivo es desconocido. |
| 1 |Conforme |El dispositivo cumple las normas. |
| 2 |No conforme |El dispositivo no es compatible. |
| 3 |Conflicto |El cumplimiento del dispositivo resultó en un conflicto. |
| 4 |Error |Se ha producido un error al leer el estado de cumplimiento del dispositivo. |


## <a name="managementstates"></a>ManagementStates

La entidad **ManagementStates** proporciona detalles sobre el estado del dispositivo. Los detalles pueden ser útiles en los casos en los que se aplican acciones remotas o el dispositivo se ha liberado o modificado.

| Propiedad  | Descripción |
|---------|------------|
| managementStateID | Identificador único del estado de administración. |
| managementStateKey | Identificador único del estado de administración en el almacenamiento de datos. Clave suplente. |
| managementStateName | Indica el estado de la acción remota aplicada a este dispositivo. |

### <a name="example"></a>Ejemplo

| managementStateID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Administrados | Administrado sin acciones remotas pendientes. |
| 1 |RetirePending | Hay un comando de retirada pendiente para el dispositivo. |
| 2 |RetireFailed | Se ha producido un error en el comando de retirada en el dispositivo. |
| 3 |WipePending | Hay un comando de borrado pendiente para el dispositivo. |
| 4 |WipeFailed | Se ha producido un error en el comando de borrado en el dispositivo. |
| 5 |Incorrecto | Estado incorrecto. |
| 6 |DeletePending | Hay un comando de eliminación pendiente para el dispositivo. |
| 7 |RetireIssued | Se ha emitido un comando de retirada en el dispositivo. |
| 8 |WipeIssued | Se ha emitido un comando de borrado. |
| 9 |WipeCanceled | Se ha cancelado un comando de borrado. |
| 10 |RetireCanceled | Se ha cancelado un comando de retirada. |
| 11 |Discovered | Intune acaba de detectar el dispositivo. Una vez que se ha registrado por primera vez, se mueve al estado administrado. |

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

La entidad **WorkPlaceJoinStateTypes** representa el estado de Workplace Join de Azure Active Directory del dispositivo.  El flujo de trabajo de inscripción puede usar uno o varios certificados para comprobar o autenticar. Cuando se inscribe un dispositivo WorkPlace, estos certificados se usan para validar el dispositivo y el usuario. La emisión de certificados se proporciona a través de un servidor SCEP (Protocolo de inscripción de certificados simple). Los valores de la entidad indican los diferentes estados en los que puede encontrarse un dispositivo durante este proceso. Algunos de estos estados incluyen el error de Workplace Join debido a un problema en la emisión de un certificado necesario (desde un servidor SCEP). Si un dispositivo no ha pasado nunca por este flujo de trabajo, el valor se establece en Desconocido.

| Propiedad  | Descripción |
|---------|------------|
| WorkPlaceJoinStateID | Identificador único del estado de Workplace Join. |
| WorkPlaceJoinStateKey | Identificador único del estado de Workplace Join en el almacenamiento de datos. Clave suplente. |
| WorkPlaceJoinStateName | Estado de Workplace Join. |

### <a name="example"></a>Ejemplo

| workPlaceJoinStateID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Unknown |Si un dispositivo no se ha unido al área de trabajo, se encuentra en estado desconocido. |
| 1 |Correcto |Unión correcta al área de trabajo. |
| 2 |FailureToGetScepMetadata |Error al obtener metadatos de SCEP. |
| 3 |FailureToGetScepChallenge |Error al obtener el desafío SCEP. |
| 4 |DeviceFailureToInstallScepCommand |Error al instalar el comando de SCEP en el dispositivo. |
| 5 |DeviceFailureToGetCertificate |El dispositivo no pudo obtener el certificado a través de SCEP. |
| 6 |DeviceScepPending |Estado pendiente. El dispositivo todavía está en el proceso de SCEP. |
| 7 |DeviceScepFailed |El dispositivo no pudo instalar el certificado a través de SCEP. |
| 8 |AADValidationFailed |No se pudo validar que el dispositivo existe en AAD. |

## <a name="managementagenttypes"></a>ManagementAgentTypes

La entidad **ManagementAgentTypes** representa los agentes usados para administrar un dispositivo.

| Propiedad  | Descripción |
|---------|------------|
| ManagementAgentTypeID | Identificador único del tipo de agente de administración. |
| ManagementAgentTypeKey | Identificador único del tipo de agente de administración en el almacenamiento de datos. Clave suplente. |
| ManagementAgentTypeName |Indica qué tipo de agente se usa para administrar el dispositivo. |

### <a name="example"></a>Ejemplo

| ManagementAgentTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 1 |EAS | El dispositivo se administra a través de Exchange Active Sync. |
| 2 |MDM | El dispositivo se administra mediante un agente MDM. |
| 3 |EasMdm | El dispositivo se administra mediante Exchange Active Sync y un agente MDM. |
| 4 |IntuneClient | El dispositivo se administra mediante el agente del equipo de Intune. |
| 5 |EasIntuneClient | El dispositivo se administra mediante Exchange Active Sync y el agente del equipo de Intune. |
| 8 |ConfigManagerClient | El dispositivo se administra mediante el agente de System Center Configuration Manager. |
| 16 |Unknown | Tipo de agente de administración desconocido. |

## <a name="devices"></a>Dispositivos

La entidad **Devices** muestra todos los dispositivos inscritos en administración y sus propiedades correspondientes.

| Propiedad  | Descripción |
|---------|------------|
| DeviceKey | Identificador único del dispositivo en el almacenamiento de datos. Clave suplente. |
| DeviceId | Identificador único del dispositivo. |
| DeviceName | Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| DeviceTypeKey | Clave del atributo de tipo de dispositivo para este dispositivo. |
| ClientRegisterationStateKey | Clave del atributo de estado de registro del cliente para este dispositivo. |
| OwnerTypeKey | Clave del atributo de tipo de propietario para este dispositivo: corporativo, personal o desconocido. |
| objectSourceKey | Ignore esta columna. |
| CreatedDate | Fecha de inscripción del dispositivo. |
| LastContact | Última inserción de dispositivo conocido en el repositorio con Intune. |
| LastContactNotification | Última vez que Intune ha notificado al dispositivo que se registre con Intune. |
| LastContactWorkplaceJoin | Marca de tiempo que indica el último estado conocido de Workplace Join para este dispositivo. |
| ManagementAgentKey | Clave del agente de administración asociado a este dispositivo. |
| ManagementStateKey | Clave del estado de administración asociado a este dispositivo, que indica el estado más reciente de una acción remota o si estaba liberado o modificado. |
| ReferenceId | Identificador del dispositivo en Azure Active Directory. |
| WorkPlaceJoinStateKey | Clave del estado de Workplace Join asociado a este dispositivo. |
| CategoryId | Ignore esta columna. |
| EnrollmentTypeKey | Clave del tipo de inscripción asociado a este dispositivo, que indica el método de inscripción. |
| CertExpirationDate | Fecha de expiración del certificado de administración de MDM. |
| MdmStatusKey | Clave para MdmStatus. |
| OSFamily | Familia de sistemas operativos (Windows, iOS, Android, etc.). |
| OSVersion | Versión del sistema operativo |
| OSMajorVersion | Componente de versión principal de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSMinorVersion | Componente de versión secundaria de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSBuildNumber | Componente de versión de compilación de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSRevisionNumber | Componente de versión de revisión de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| EasID | Identificador de EAS de este dispositivo, si está administrado mediante Exchange Active Sync. |
| GraphDeviceIsManaged | Último estado de administración que Intune ha establecido en Azure AD. |
| GraphDeviceIsCompliant | Último estado de cumplimiento que Intune ha establecido en Azure AD. |
| SerialNumber | Número de serie del dispositivo, si está disponible. |
| EnrolledByUser | Identificador del usuario que ha inscrito el dispositivo, que hace referencia a la columna userId de la tabla de usuario. |
| RowLastModifiedDateTimeUTC | Fecha y hora de la última modificación de este registro. |
| ProcessorArchitecture | Arquitectura de procesador. |
| DeviceAction | Última acción de dispositivo emitida. Ignórela por el momento. |
| Fabricante | Fabricante del dispositivo. |
| Modelo | Modelo del dispositivo. |
| LastPolicyUpdateUtc | Hora más reciente en la que se ha actualizado la directiva del dispositivo. |
| LastExchangeStatusUtc | Hora más reciente en la que se ha sincronizado el dispositivo con Exchange. |
| IsDeleted | Establecido en True si el dispositivo ya no se administra mediante Intune. Conserva el último estado conocido. |
| AndroidSecurityPatchLevel |La fecha de la revisión de seguridad más reciente del dispositivo. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

La entidad **DevicePropertyHistory** tiene las mismas propiedades que las tablas de dispositivos y las instantáneas diarias de cada registro de dispositivo por día de los últimos 90 días. La columna DateKey indica el día de cada fila.

| Propiedad  | Descripción |
|---------|------------|
| DateKey |Referencia a la tabla de fechas que indica el día. |
| DeviceKey |Identificador único del dispositivo en el almacenamiento de datos. Clave suplente. Se trata de una referencia a la tabla de dispositivos que contiene el identificador de dispositivo de Intune. |
| DeviceName |Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| DeviceTypeKey |Clave del atributo de tipo de dispositivo para este dispositivo. |
| ClientRegisterationStateKey |Clave del atributo de estado de registro del cliente para este dispositivo. |
| OwnerTypeKey |Clave del atributo de tipo de propietario para este dispositivo: corporativo, personal o desconocido. |
| objectSourceKey |Ignore esta columna. |
| CreatedDate |Fecha de inscripción del dispositivo. |
| LastContact |Última inserción de dispositivo conocido en el repositorio con Intune. |
| LastContactNotification |Última vez que Intune ha notificado al dispositivo que se registre con Intune. |
| LastContactWorkplaceJoin |Marca de tiempo que indica el último estado conocido de Workplace Join para este dispositivo. |
| ManagementAgentKey |Clave del agente de administración asociado a este dispositivo. |
| ManagementStateKey |Clave del estado de administración asociado a este dispositivo, que indica el estado más reciente de una acción remota o si estaba liberado o modificado. |
| ReferenceId |Identificador del dispositivo en Azure Active Directory. |
| WorkPlaceJoinStateKey |Clave del estado de Workplace Join asociado a este dispositivo. |
| CategoryId |Ignore esta columna. |
| EnrollmentTypeKey |Clave del tipo de inscripción asociado a este dispositivo, que indica el método de inscripción. |
| CertExpirationDate |Fecha de expiración del certificado de administración de MDM. |
| MdmStatusKey |Clave para MdmStatus. |
| OSFamily |Familia de sistemas operativos (Windows, iOS, Android, etc.). |
| OSVersion |Versión del SO. |
| OSMajorVersion |Componente de versión principal de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSMinorVersion |Componente de versión secundaria de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSBuildNumber |Componente de versión de compilación de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSRevisionNumber |Componente de versión de revisión de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| EasID |Identificador de EAS de este dispositivo, si está administrado mediante Exchange Active Sync. |
| GraphDeviceIsManaged |Último estado de administración que Intune ha establecido en Azure AD. |
| GraphDeviceIsCompliant |Último estado de cumplimiento que Intune ha establecido en Azure AD. |
| SerialNumber |Número de serie del dispositivo, si está disponible. |
| EnrolledByUser |Identificador del usuario que ha inscrito el dispositivo, que hace referencia a la columna userId de la tabla de usuario. |
| RowLastModifiedDateTimeUTC |Fecha y hora de la última modificación de este registro. |
| ProcessorArchitecture |Arquitectura de procesador. |
| DeviceAction |Última acción de dispositivo emitida. Ignórela por el momento. |
| Fabricante |Fabricante del dispositivo. |
| Modelo |Modelo del dispositivo. |
| LastPolicyUpdateUtc |Hora más reciente en la que se ha actualizado la directiva del dispositivo. |
| LastExchangeStatusUtc |Hora más reciente en la que se ha sincronizado el dispositivo con Exchange. |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

La entidad **MdmDeviceInventoryHistories** contiene instantáneas diarias de los datos del inventario para dispositivos administrados por MDM durante los últimos 90 días. La columna DateKey indica el día de la fila. Es posible que algunas propiedades no se puedan aplicar o rellenar para todos los dispositivos, por lo que debe consultar esta página. Para obtener más información, vea [Comprender el funcionamiento de sus dispositivos mediante el inventario en Microsoft Intune](device-inventory.md).

| Propiedad  | Descripción |
|---------|------------|
| DateKey | Referencia a la tabla de fechas que indica el día. |
| DeviceKey |Identificador único del dispositivo en el almacenamiento de datos. Clave suplente. Se trata de una referencia a la tabla de dispositivos que contiene el identificador de dispositivo de Intune. |
| DeviceModel |Modelo del dispositivo. |
| Sistema operativo |Sistema operativo del dispositivo. |
| DeviceName |Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| SoftwareVersion |En la mayoría de los casos es la versión del sistema operativo, excepto en plataformas de Apple, en cuyo caso es diferente de la versión del sistema operativo. |
| Imei |Número IMEI. |
| HardwareInventoryTimeUtc |Primera vez que se notificó el inventario de este dispositivo. |
| InventoryModifiedTimeUtc |Última vez que se almacenó el inventario al tomarse esta instantánea. |
| InventoryReportingTimeUtc |Última vez que se recopiló el inventario de este dispositivo. |
| ExchangeActiveSyncId |Identificador de dispositivo de Exchange ActiveSync. |
| ComputerSystemDescription |Descripción del sistema. |
| ComputerSystemName |Nombre del sistema. |
| ComputerSystemManufacturer |Fabricante del sistema. |
| ComputerSystemModel |Modelo del sistema. |
| UserName |Nombre de usuario. |
| OSType |Tipo de sistema operativo. |
| OSCaption |Título del sistema operativo. |
| OSName |Nombre del sistema operativo. |
| OSManufacturer |Fabricante del sistema operativo. |
| OSProductSuite |Conjunto de productos del sistema operativo. |
| OSProductType |Tipo de producto del sistema operativo. |
| Configuración regional |Configuración regional del sistema operativo. |
| PhysicalMemoryCapacity |Capacidad de memoria física (en bytes). |
| PhysicalMemoryRemovable |Memoria física extraíble (en bytes). |
| SystemEnclosureChassisTypesInnerText |Define el tipo de chasis del sistema para este dispositivo. Los números indican los valores siguientes:  <br>0 o vacío = desconocido   <br>1 = es un equipo de escritorio   <br>2 = es un portátil  <br>3 = es una estación de trabajo  <br>4 = es un servidor de empresa  <br>100 = es un teléfono  <br>101 = es una tableta  <br>102/103 = otro tipo desconocido de dispositivo móvil |
| SystemEnclosureModel |Modelo de revestimiento de hardware del sistema. |
| SystemEnclosureSerialNumber |Número de serie del revestimiento de hardware del sistema. |
| NetworkAdapterConfigurationText |Texto de configuración del adaptador de red. |
| MacAddress |Dirección MAC. |
| SmsID |Identificador de dispositivo de Intune. |
| CertExpiry |Fecha de expiración del certificado de administración de MDM. |
| DeviceClientAgentVersion |Versión del agente de cliente. |
| DeviceClientID |Identificador de cliente del dispositivo. |
| SerialNumber |Número de serie. |
| DeviceManufacturer |Fabricante del dispositivo. |
| DMVersion |Versión de DM. |
| FirmwareVersion |Versión de firmware. |
| HardwareVersion |Versión de hardware. |
| PlatformType |Tipo de plataforma. |
| ProcessorLevel |Nivel de procesador. |
| ProcessorRevision |Revisión del procesador. |
| Product |Producto. |
| ProductVersion |Versión del producto. |
| OEM |Fabricante de equipo original. |
| DeviceBuildVersion |Versión de compilación del dispositivo. |
| Meid |Identificador de equipo móvil. |
| PhoneNumber |Número de teléfono. |
| SubscriberCarrierNetwork |Nombre de red del operador de telefonía. |
| CellularTechnology |Tipo de red del operador de telefonía (CDMA/GSM). |
| Imsi |Número IMSI. |
| JailBroken |True si el dispositivo está liberado o modificado. |
| IsActivationLockEnabled |True si el bloqueo de activación está habilitado. |
| DeviceType |Tipo de dispositivo |
| IsSupervised |Está supervisado |
| DeviceDisplayNumberOfColors |Número de colores de la pantalla del dispositivo. |
| HorizontalResolution |Resolución de pantalla horizontal del dispositivo. |
| VerticalResolution |Resolución de pantalla vertical del dispositivo. |
| StorageFree |Almacenamiento libre (en bytes). |
| StorageTotal |Almacenamiento total (en bytes). |
| ProgramFree |Memoria de programa libre (en bytes). |
| ProgramTotal |Memoria de programa total (en bytes). |
| RemovableStorageFree |Almacenamiento extraíble libre (en bytes). |
| RemovableStorageTotal |Almacenamiento extraíble total (en bytes). |
| DeviceMemoryDeviceCapacity |Capacidad de memoria del dispositivo. |
| DeviceMemoryAvailableDeviceCapacity |Capacidad disponible de memoria del dispositivo. |
| DeviceOSVersion |Versión del SO |
| DeviceOSPlatform |Plataforma del sistema operativo. |
| DeviceOSLanguage |Idioma del sistema operativo. |
| PasswordMaxAttemptsBeforeWipe |Número máximo de intentos de contraseña permitidos antes de que se produzca el borrado del dispositivo. |
| PasswordMinComplexChars |Número mínimo de caracteres complejos que se requieren en la contraseña. |
| PasswordMinLength |Longitud mínima necesaria de la contraseña. |
| PasswordHistory |Contraseña: número mínimo de contraseñas históricas que no se aceptan. |
| PasswordEnabled |Contraseña: ¿habilitada? |
| PasswordExpiration |Contraseña: fecha de expiración. |
| AllowRecoveryPassword |Permitir recuperación de contraseña. |
| PasswordAutoLockTimeout |Contraseña: tiempo de espera de bloqueo automático. |
| PasswordType |Tipo de contraseña. |
| BacklightACTimeout |Tiempo de espera de retroiluminación cuando se está conectado a una fuente de alimentación. |
| BacklightBatTimeout |Tiempo de espera de retroiluminación con batería. |
| PowerBackupPercent |Porcentaje de energía de reserva. |
| BatteryPercent |Porcentaje de batería restante. |
| PlatformID |Identificador de plataforma. |
| ExchangeDeviceID |Identificador de dispositivo de Exchange. |
| SmsProcessorDescription |Descripción del procesador. |
| OwnerEmailAddress |Dirección de correo electrónico del propietario. |
| DeviceOSName |Nombre del sistema operativo. |
| WifiMac |Dirección MAC de la Wi-Fi. |
| EthernetMac |Dirección MAC de Ethernet. |
| RequireEncryption |Indica si el dispositivo está cifrado. |
| ActivationLockBypassCode |Código de omisión del bloqueo de activación. |

## <a name="applicationinventory"></a>ApplicationInventory

La entidad **ApplicationInventory** muestra las aplicaciones que se encuentran en el dispositivo en el momento de recopilación del inventario.


|      Propiedad      |                       Descripción                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              Referencia a la tabla de dispositivos.               |
|   ApplicationKey   | ? (copiado de ExchangeDeviceService\DeviceApplication). |
|  ApplicationName   | ? (copiado de ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion | ? (copiado de ExchangeDeviceService\DeviceApplication). |
|     BundleSize     | ? (copiado de ExchangeDeviceService\DeviceApplication). |

