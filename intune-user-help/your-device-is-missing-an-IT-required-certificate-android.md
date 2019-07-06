---
title: El dispositivo no tiene un certificado | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6bdf97e6a36a49bc6df5a182af7676c357440f3e
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529329"
---
# <a name="your-android-device-is-missing-a-certificate-required-by-your-company-support"></a>El dispositivo Android no tiene un certificado que necesita el equipo de soporte técnico de su empresa

Si el dispositivo no está inscrito en Intune y no tiene un certificado determinado que necesita el equipo de soporte técnico de su empresa, no podrá iniciar sesión en la aplicación de Portal de empresa. Cuando intente iniciar sesión, verá el siguiente mensaje:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Para resolver este problema y obtener el certificado necesario, hay dos pasos principales que necesitará seguir:

- Identificar el certificado que falta mirando en el equipo de una empresa o escuela.
- Usar el dispositivo para descargar el certificado que falta desde Internet.

## <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>Identificar el certificado que falta mirando en el equipo de una empresa o escuela

1. Abra un equipo y, luego, Internet Explorer. Si no tiene un equipo para esto, póngase en contacto con el equipo de soporte técnico de su empresa. Para encontrar la información de contacto del equipo de soporte técnico de su empresa, vaya al [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).

2. Vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) e inicie sesión con sus credenciales profesionales o educativas.

3. A la derecha de la barra de direcciones del explorador, elija el símbolo que parece un candado como se muestra en la siguiente captura de pantalla.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    Si no ve el símbolo del candado, deténgase y póngase en contacto con el equipo de soporte técnico de su empresa. El candado significa que la sesión iniciada es segura, por lo que no debe continuar a menos que vea dicho símbolo.

4. Elija **Ver certificados**.

    ![screenshot-internet-explorer-view-certificases-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. En el cuadro de diálogo **Certificado**, elija la pestaña **Ruta de certificación** y, luego, identifique el certificado que tiene que obtener desde Internet. El nombre del certificado que necesita estará en la misma posición que el que está resaltado en la captura de pantalla del ejemplo anterior.

## <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>Descargar e instalar el certificado que falta en el dispositivo móvil Android

1. Con un motor de búsqueda como Bing o Google, busque el nombre del certificado que falta que identificó en la sección anterior. El certificado puede terminar con diferentes "extensiones", como ".crt", ".pem", etc.

2. Descargue el certificado raíz desde el sitio web.

3. Una vez que descargue el certificado, arrastre hacia abajo desde la parte superior del dispositivo para abrir las notificaciones y luego pulse el nombre del certificado en la lista de notificaciones.

4. En el cuadro de diálogo **Nombre del certificado** que se muestra en la siguiente captura de pantalla, acepte el nombre de certificado predeterminado.

5. Asegúrese de que **Uso de credencial** está configurado como **Usada para VPN y aplicaciones** y pulse en **Aceptar**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Cierre la aplicación del portal de empresa.

7. Vuelva a abrir la aplicación del portal de empresa. Ahora debería poder iniciar sesión en la aplicación Portal de empresa. Si necesita ayuda, póngase en contacto con el equipo de soporte técnico de su empresa.

Si aparece el mismo mensaje que indica que "falta un certificado" como el que se ha mostrado anteriormente, y ya ha seguido el procedimiento, probablemente todavía haya otro certificado que el equipo de soporte técnico de su empresa necesitará ayudarle a instalar. Póngase en contacto con el equipo de soporte técnico de su empresa para obtener ayuda con la información de contacto disponible en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
