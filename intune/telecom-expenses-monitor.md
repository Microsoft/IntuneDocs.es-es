---
title: Configurar un servicio de administración de gastos de telecomunicaciones
titleSuffix: Microsoft Intune
description: Integre Intune con el servicio de administración de gastos de telecomunicaciones de Saaswedo.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 031db83302dfef8b99fc83ab7975e233c3eeb799
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57396869"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Configuración de un servicio de administración de gastos de telecomunicaciones en Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune permite administrar los gastos de telecomunicaciones derivados del uso de datos en dispositivos móviles empresariales. Para ello, Intune se ha integrado con la solución de [administración de gastos de telecomunicaciones Datalert](http://datalert.biz/get-started) del desarrollador de software externo Saaswedo. Datalert es un software de administración de gastos de telecomunicaciones en tiempo real que le permite administrar el uso de datos de telecomunicaciones. Le ayuda a evitar datos costosos e inesperados y usos de itinerancia por encima del límite de los dispositivos administrados por Intune.

La integración de Intune con Datalert le permite establecer, supervisar y aplicar de forma centralizada límites para el uso de datos nacionales y de itinerancia. Se desencadenan alertas automatizadas cuando los límites superan los umbrales definidos. Puede configurar el servicio para que se apliquen diferentes acciones sobre individuos o grupos de usuarios finales (por ejemplo, deshabilitar la itinerancia o superar el umbral). Además, en la consola de administración de Datalert se pueden encontrar informes que proporcionan información sobre la supervisión y el uso de datos.

En el siguiente diagrama se muestra cómo se integra Intune con Datalert.

  ![Diagrama de integración de Intune y Datalert](./media/tem-datalert-intune-solution-diagram.png)

Para poder usar el servicio Datalert con Intune, debe realizar configuraciones en la consola de Datalert y en Intune. La conexión debe estar activada para el servicio Datalert y para Intune. Si está habilitado el lado de la conexión de Datalert, pero no el de Intune, este último recibe la comunicación, pero la ignora.

## <a name="supported-platforms"></a>Plataformas compatibles

- Samsung Knox
- iOS 8.0 y versiones posteriores

## <a name="prerequisites"></a>Requisitos previos

- Una suscripción a Microsoft Intune y acceso a Azure Portal.
- Suscripción al servicio de administración de gastos de telecomunicaciones Datalert.

## <a name="list-of-telecom-expense-management-providers"></a>Lista de proveedores de administración de gastos de telecomunicaciones

Intune se integra actualmente con los siguientes proveedores de administración de gastos de telecomunicaciones:

[Servicio de administración de gastos de telecomunicaciones Datalert de Saaswedo](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>Implementar la solución integrada de Intune y Datalert

Antes de empezar, asegúrese de tener una suscripción al servicio de administración de gastos de telecomunicaciones Datalert y a Intune.

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>Paso 1: Conectar el servicio Datalert a Microsoft Intune

1. Inicie sesión en la consola de administración de Datalert con sus credenciales de administrador.

2. En la consola de administración de Datalert, vaya a la ficha **Settings** (Configuración) y, luego, a **MDM configuration** (Configuración de MDM).

3. Seleccione **Desbloquear** en la parte inferior de la página para modificar la configuración de la página.

4. En la sección **Intune / Datalert Connection** (Intune / Conexión de Datalert), elija **Microsoft Intune** para **Server MDM** (MDM de servidor).    

5. Para **Dominio de Azure AD**, escriba su identificador de inquilino de Azure y seleccione **Conexión**.

    Al seleccionar **Conexión**, el servicio Datalert se pone en contacto con Intune para asegurarse de que no haya ninguna conexión existente de Datalert con Intune. Al cabo de unos segundos, aparece una página de inicio de sesión de Microsoft, seguida de la autenticación de Azure para Datalert.

6. En la página de autenticación de Microsoft, seleccione **Aceptar**. Se le redirigirá a una página de Datalert donde se le dan las **gracias** y que se cierra transcurridos unos segundos. Datalert valida la conexión y muestra marcas de verificación verdes junto a una lista de elementos que se han validado. Si se produce un error en la validación, aparece un mensaje en rojo y debe ponerse en contacto con el soporte técnico de Datalert para obtener ayuda.

    En la siguiente captura de pantalla se muestran las marcas de verificación verdes que aparecen cuando la conexión se realiza correctamente.

   ![Página de Datalert en la que se muestra una conexión correcta](./media/tem-datalert-connection.png)

7. En la sección **Datalert App / ADAL Consent** (Aplicación Datalert / Consentimiento ADAL), establezca el conmutador en **Activo**. En la página de autenticación de Microsoft, seleccione **Aceptar**. Se le redirigirá a una página de Datalert donde se le dan las **gracias** y que se cierra transcurridos unos segundos. Datalert valida la conexión y muestra marcas de verificación verdes junto a una lista de elementos que se han validado. Si se produce un error en la validación, aparece un mensaje en rojo y debe ponerse en contacto con el soporte técnico de Datalert para obtener ayuda.    

    En la siguiente captura de pantalla se muestran las marcas de verificación verdes que aparecen cuando la conexión se realiza correctamente.

   ![Página de Datalert en la que se muestra una conexión correcta](./media/tem-datalert-adal-consent.png)

8. En la sección **MDM Profiles management (optional)** (Administración de perfiles de MDM (opcional)), establezca el conmutador en **Activo** para permitir que Datalert lea los perfiles disponibles en Intune, de modo que le ayude a configurar las directivas. En la página de autenticación de Microsoft, seleccione **Aceptar**. Se le redirigirá a una página de Datalert donde se le dan las **gracias** y que se cierra transcurridos unos segundos. Datalert valida la conexión y muestra marcas de verificación verdes junto a una lista de elementos que se han validado. Si se produce un error en la validación, aparece un mensaje en rojo y debe ponerse en contacto con el soporte técnico de Datalert para obtener ayuda.    

    En la siguiente captura de pantalla se muestran las marcas de verificación verdes que aparecen cuando la conexión se realiza correctamente.

   ![Página de Datalert en la que se muestra una conexión correcta](./media/tem-datalert-mdm-profiles.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>Paso 2: Comprobar que la característica de administración de gastos de telecomunicaciones está activa en Intune

Tras completar el paso 1, la conexión debe haberse habilitado automáticamente y se debe mostrar el estado de conexión **Activo** en Azure Portal. En estos pasos se indica cómo buscar el estado **Activo**.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.

3. En el panel **Intune**, elija **Configuración del dispositivo**.

4. En el panel **Configuración del dispositivo**, elija **Configuración** > **Administración de gastos de telecomunicaciones**.

   Busque el estado de conexión **Activo** en la parte superior de la página.

   ![Página de Intune en la que se muestra el estado de conexión Activo de Datalert](./media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>Paso 3: Implementar la aplicación Datalert en dispositivos empresariales inscritos

Para asegurarse de que solo se recopila el uso de datos de las líneas empresariales, debe realizar estas dos acciones:
- Crear categorías de dispositivos en Intune.
- Establecer los teléfonos empresariales como el único destino de la aplicación Datalert.

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>Definir categorías de dispositivos y grupos de dispositivos asignados a las categorías

En función de las necesidades de su organización, cree al menos dos categorías de dispositivos (por ejemplo, Empresarial y Personal). Después, cree grupos de dispositivos dinámicos para cada categoría. Puede crear más categorías para su organización, según resulte necesario.

Estas categorías se mostrarán a los usuarios durante la inscripción. Dependiendo de la categoría que estos elijan, el dispositivo inscrito se trasladará al grupo de dispositivos correspondiente. Para obtener más información sobre cómo crear categorías de dispositivos, consulte [Map devices to groups](device-group-mapping.md) (Asignar dispositivos a grupos).

  ![Captura de pantalla del panel Agregar directiva](./media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Crear la aplicación Datalert en Intune

Siga estos pasos para crear la aplicación Datalert en Intune para cada plataforma. En estos pasos se utiliza iOS como ejemplo.

1. En el panel **Intune** de [Azure Portal](https://portal.azure.com), elija **Aplicaciones cliente**.

2. En el panel **Aplicaciones cliente**, elija **Administrar** > **Aplicaciones**.

3. Seleccione **Agregar** para agregar una aplicación.

4. Seleccione el tipo de aplicación. Por ejemplo, para iOS, seleccione **Aplicación de la tienda iOS**.

5. En **Buscar en App Store**, escriba **Datalert** en la ventana de búsqueda para buscar dicha aplicación.

6. Seleccione la aplicación **Datalert** y, luego, **Seleccionar**.

   ![Captura de pantalla del panel Agregar directiva](./media/tem-select-app-from-apple-app-store.png)

7. Complete los pasos restantes para crear una aplicación para iOS.

   ![Captura de pantalla del panel Agregar directiva](./media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Asignar la aplicación Datalert al grupo de dispositivos empresariales

1. En el panel **Aplicaciones cliente: aplicaciones**, seleccione la aplicación de iOS Datalert que ha creado en el paso anterior.

2. En el panel **Aplicaciones**, elija **Administrar** > **Asignaciones**.

3. Elija **Agregar grupo** y siga los pasos para seleccionar el grupo de dispositivos empresariales.

4. Elija si quiere que sea obligatorio u opcional instalar la aplicación para el grupo. En la siguiente captura de pantalla de ejemplo se muestra la instalación como un paso obligatorio, lo que implica que los usuarios deben instalar la aplicación Datalert después de inscribir sus dispositivos.

   ![Captura de pantalla del panel Agregar directiva](./media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>Paso 4: Agregar líneas de teléfono empresariales de pago a la consola de Datalert

Llegado este paso, ya habrá configurado los servicios Intune y Datalert para que se comuniquen entre sí. Ahora debe agregar las líneas de teléfono empresariales de pago a la consola de Datalert, y definir umbrales y acciones para las posibles infracciones del uso de la itinerancia o los datos móviles. Puede agregar manualmente líneas telefónicas corporativas de pago a la consola de Datalert o puede agregarlas automáticamente una vez que el dispositivo se inscribe en Intune.

Para configurar estos elementos, vaya a la [página de configuración de Datalert para Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (http://www.datalert.fr/microsoft-intune/intune-setup) y siga los pasos del asistente para la configuración, en la pestaña **Settings** (Configuración).

  ![Captura de pantalla del panel Agregar directiva](./media/tem-add-phone-lines-to-datalert-console.png)


El servicio Datalert ya está activo y comienza la supervisión del uso de datos y la deshabilitación de datos móviles y de itinerancia en los dispositivos que superan los límites de uso configurados.

## <a name="client-enrollment-experience"></a>Experiencia de inscripción de cliente
Consulte lo siguiente para ver la experiencia de inscripción de cliente:
-   [Inscripción del dispositivo iOS en la administración de gastos de telecomunicaciones](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-   [Inscripción del dispositivo Android en la administración de gastos de telecomunicaciones](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>Desactivar el servicio Datalert

Si deshabilita el servicio Datalert en Azure Portal:

- Todas las acciones que se hayan aplicado a los dispositivos, a consecuencia de las pasadas infracciones de los límites de uso, se desharán.
- Ya no se bloqueará para los usuarios el acceso a los datos y la itinerancia.
- Intune seguirá recibiendo señales del servicio, pero las ignorará.

**Para desactivar el servicio**

1. En el panel **Administración de gastos de telecomunicaciones** de Azure Portal, seleccione **Deshabilitar**.

2. Seleccione **Guardar**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Ver informes de uso de datos e itinerancia

En este momento, los informes de uso de datos solo están disponibles en la consola de administración de Datalert de Saaswedo.

Próximamente se agregarán las instrucciones que deben seguir los usuarios finales para instalar la aplicación Datalert.
