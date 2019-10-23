---
title: Integración de Windows Hello para empresas con Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo crear una directiva para controlar el uso de Windows Hello para empresas en dispositivos administrados".
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: ed3152a6717898aa1f758fb06a5f701048aebed4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508768"
---
# <a name="integrate-windows-hello-for-business-with-microsoft-intune"></a>Integración de Windows Hello para empresas con Microsoft Intune  


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede integrar Windows Hello para empresas (anteriormente Microsoft Passport for Work) con Microsoft Intune.

 Hello para empresas es un método alternativo de inicio de sesión que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, tarjeta inteligente o tarjeta inteligente virtual. Permite usar un *gesto de usuario* para iniciar sesión, en lugar de una contraseña. Un gesto de usuario podría ser una autenticación biométrica de PIN simple, como Windows Hello, o un dispositivo externo como un lector de huellas digitales.

Intune se integra con Hello para empresas de dos maneras:

- Se puede crear una directiva de Intune en **Inscripción de dispositivos**. Esta directiva se destina a toda la organización (a todos los inquilinos). Es compatible con la configuración rápida (OOBE) de Windows AutoPilot y se aplica cuando se inscribe un dispositivo. 
- Se puede crear un perfil de protección de identidad en **Configuración del dispositivo**. Este perfil se destina a los usuarios y dispositivos asignados, y se aplica durante la inserción en el repositorio. 

Use este artículo para crear una directiva de Windows Hello para empresas predeterminada destinada a toda la organización. Para crear un perfil de protección de identidad que se aplique a grupos de usuarios y dispositivos concretos, vea [Configuración de un perfil de protección de identidad](identity-protection-configure.md).  

<!--- - You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> En las versiones de escritorio y móvil de Windows 10 anteriores a la Actualización de aniversario, era posible establecer dos PIN diferentes para autenticarse en los recursos:
> - El **PIN de dispositivo** se usaba para desbloquear el dispositivo y conectarse a recursos de nube.
> - El **PIN de trabajo** se usaba para acceder a recursos de Azure AD en los dispositivos personales del usuario (BYOD).
> 
> En la Actualización de aniversario, estos dos PIN se combinaron en un solo PIN de dispositivo.
> Las directivas de configuración de Intune que establezca para controlar el PIN de dispositivo y las directivas de Windows Hello para empresas que configure serán las que establecerán ahora este nuevo valor de PIN.
> Si ha establecido que ambos tipos de directivas controlarán el PIN, la directiva de Windows Hello para empresas se aplicará en los dispositivos móviles y de escritorio Windows 10.
> Para garantizar que se resuelven los conflictos de directivas y que la directiva de PIN se aplica correctamente, actualice su directiva de Windows Hello para empresas de modo que coincida con la configuración de la directiva de configuración y pídales a los usuarios que sincronicen sus dispositivos en la aplicación del portal de empresa.



## <a name="create-a-windows-hello-for-business-policy"></a>Crear una directiva de Windows Hello para empresas

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Vaya a **Inscripción de dispositivos** > **Inscripción de Windows** > **Windows Hello para empresas**. Se abre el panel de Windows Hello para empresas.

3. En **Configurar Windows Hello para empresas**, seleccione entre las opciones siguientes.

    - **Deshabilitado**. Si no quiere usar Windows Hello para empresas, seleccione esta opción. Si está deshabilitada, los usuarios no pueden aprovisionar Windows Hello para empresas excepto en teléfonos móviles unidos a Azure Active Directory donde puede ser necesario el aprovisionamiento.
    - **Habilitado**. Seleccione esta opción si quiere configurar Windows Hello para empresas.  Cuando se selecciona *Habilitado*, los otros valores de configuración de Windows Hello se vuelven visibles. 
    - **No configurado**. Seleccione esta opción si no quiere usar Intune para controlar la configuración de Windows Hello para empresas. No se cambiará ninguna de las opciones de configuración de Windows Hello para empresas en los dispositivos Windows 10. Todas las demás configuraciones del panel no están disponibles.

4. Si ha seleccionado **Habilitado** en el paso anterior, configure las opciones necesarias que se aplicarán en todos los dispositivos Windows 10 y Windows 10 Mobile inscritos. Después de configurar estos valores, seleccione **Guardar**.

   - **Usar un Módulo de plataforma segura (TPM)** :  
     Un chip de TPM ofrece una capa adicional de seguridad de datos. Elija uno de los siguientes valores:

     - **Requerido** (valor predeterminado). Solo los dispositivos que tengan un TPM accesible pueden aprovisionar Windows Hello para empresas.
     - **Preferido**. Los dispositivos intentan primero usar un TPM. Si no está disponible, pueden usar el cifrado de software.

   - **Longitud mínima de PIN** y **Longitud máxima de PIN**:  
     Configura los dispositivos para que usen las longitudes de PIN mínima y máxima que se especifiquen, lo cual garantiza un inicio de sesión seguro. La longitud predeterminada del PIN es de seis caracteres, pero se puede aplicar una longitud mínima de cuatro. La longitud de PIN máxima es de 127 caracteres.

   - **Letras minúsculas en el PIN**, **Letras mayúsculas en el PIN** y **Caracteres especiales en el PIN**.  
     Si quiere aplicar un PIN más seguro, puede requerir el uso de letras mayúsculas, letras minúsculas y caracteres especiales en el PIN. Para cada una, seleccione entre:

     - **Permitido**. Los usuarios pueden usar el tipo de carácter en el PIN, pero no es obligatorio.

     - **Requerido**. Los usuarios deben incluir al menos uno de los tipos de carácter en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.

     - **No permitido** (valor predeterminado). Los usuarios no deben usar estos tipos de caracteres en el PIN. (Este es también el comportamiento si no se configura esta opción).   

       Entre los caracteres especiales se incluyen los siguientes: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **Expiración del PIN (días)** :  
     Se recomienda especificar un período de expiración del PIN, transcurrido el cual hay que cambiarlo. El valor predeterminado es 41 días.

   - **Recordar historial de PIN**:  
     Restringe la reutilización de los PIN usados anteriormente. De forma predeterminada, no se pueden volver a usar los últimos cinco PIN.

   - **Permitir autenticación biométrica**:  
     Habilita la autenticación biométrica, como el reconocimiento facial o la huella digital, como alternativa a un PIN para Windows Hello para empresas. Los usuarios todavía deben configurar un PIN de trabajo por si produce un error en la autenticación biométrica. Elija de entre las siguientes opciones:

     - **Sí**. Windows Hello para empresas permite la autenticación biométrica.
     - **No**. Windows Hello para empresas impide la autenticación biométrica (en todos los tipos de cuenta).

   - **Usar tecnología mejorada de suplantación de identidad cuando esté disponible**:  
     Establece si se van a usar las características contra la suplantación de identidad de Windows Hello en los dispositivos que lo permitan (por ejemplo, cuando se detecte una fotografía de un rostro en lugar de un rostro real).  

     Cuando esta opción se establece en **Sí**, Windows exige que todos los usuarios usen tecnología contra la suplantación de identidad en características faciales cuando se admitan.

   - **Permitir inicio de sesión por teléfono**:  
     Si esta opción se establece en **Sí**, los usuarios pueden usar una cuenta de Passport remota para que actúe como dispositivo complementario portátil para la autenticación del equipo de escritorio. El equipo de escritorio debe estar unido a Azure Active Directory y el dispositivo complementario debe configurarse con un PIN de Windows Hello para empresas.

## <a name="windows-holographic-for-business-support"></a>Compatibilidad con Windows Holographic for Business

Windows Holographic for Business es compatible con las siguientes opciones de configuración de Windows Hello for Business:

- Usar un Módulo de plataforma segura (TPM)
- Longitud mínima del PIN
- Longitud máxima del PIN
- Minúsculas en el PIN
- Mayúsculas en el PIN
- Caracteres especiales en el PIN
- Expiración del PIN (días)
- Recordar historial de PIN

## <a name="further-information"></a>Más información
Para más información sobre Windows Hello para empresas, consulte [la guía](https://technet.microsoft.com/library/mt589441.aspx) de la documentación de Windows 10.
