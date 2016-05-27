---
# required metadata

title: Descripción del servicio | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Descripción del servicio Microsoft Intune

Microsoft Intune es un servicio basado en la nube que le ayuda a administrar equipos con Windows, iOS, Android y dispositivos móviles de Windows. Asimismo, Intune le ayudará a proteger los datos y las aplicaciones de su empresa. Puede usar Intune por sí solo o puede integrarlo con System Center 2012 R2 Configuration Manager para ampliar sus capacidades de administración.

Microsoft le ofrece los beneficios propios de la incorporación a Intune para aquellos servicios válidos que se encuentren en planes aptos. El beneficio de incorporación le permite trabajar de forma remota con los especialistas de Microsoft para preparar el entorno de Intune para su uso. Para más información, consulte [Descripción del beneficio de servicio de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=619281)..

Puede comenzar a usar Intune con una versión de evaluación gratuita de 30 días que incluye 100 licencias de usuario. Para iniciar la versión de prueba gratuita, [haga clic aquí para visitar la página de registro de Intune](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/). Si su organización tiene un contrato Enterprise o el contrato de licencias por volumen equivalente, póngase en contacto con su representante de Microsoft para configurar la versión de evaluación gratuita.

> [!NOTE]
> Si su organización tiene una cuenta profesional o educativa de Microsoft Online Services y es posible que continúe con esta suscripción de Intune en producción una vez finalizado el período de evaluación, debe hacer clic en la opción **Iniciar sesión** de esa página y autenticarse con la cuenta de administrador global de su organización. Esta acción garantizará que su versión de evaluación de Intune se vincula con su cuenta de trabajo o académica existente.

Para obtener una lista de las opciones que puede configurar en los dispositivos móviles, consulte:

-   [Capacidades de administración de dispositivos móviles en Microsoft Intune](mobile-device-management-capabilities-in-microsoft-intune.md)

-   [Configuración general para dispositivos móviles en Configuration Manager](https://technet.microsoft.com/en-us/library/dn376523.aspx)

Para más información sobre System Center 2012 R2 Configuration Manager, consulte [Biblioteca de documentación de System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx)..

## Información acerca de cómo le afectan las actualizaciones del servicio de Intune
Dado que Intune es un servicio en línea, Microsoft puede actualizarlo de forma periódica.

Use la información de este tema para comprender mejor con qué frecuencia se realizan estas actualizaciones de servicio y cómo son las notificaciones que le enviamos cuando una actualización puede afectar a su uso del servicio.

Para conocer más detalles sobre los cambios en el servicio de Intune, consulte [Novedades de Microsoft Intune](/intune/deploy-use/Whats-new-in-microsoft-intune.md). En el [Blog de Microsoft Intune](http://blogs.technet.com/b/microsoftintune/) también se describen los cambios que se realizan en el servicio y se proporcionan sugerencias útiles para permitirle sacar el máximo provecho a Intune.

Asimismo, las actualizaciones importantes del servicio se le comunicarán directamente desde la consola de Intune en el tablón de anuncios.

Estos son los tipos de notificaciones que Microsoft proporciona sobre el servicio Intune:
-   Para ayudarle a planear los cambios de servicio, le notificamos con un plazo mínimo de entre 30 y 90 días antes de la actualización del servicio, dependiendo del impacto del cambio. Esto ocurrirá al usar canales de comunicación del producto como las alertas del tablón de anuncios. Entre estos cambios se incluyen los siguientes:
* Actualizaciones que podrían tener algún impacto en las disposiciones legales o en su cumplimiento
* Cambios en la experiencia de usuario, la interfaz de usuario y los flujos de trabajo
* API nuevas o modificadas: recibirá una notificación indicándole que necesita probar las aplicaciones personalizadas para garantizar la compatibilidad con versiones anteriores
* Cambios en los requisitos del sistema, por ejemplo, la versión mínima necesaria del explorador
* Cualquier actualización que requiera que tome medidas para habilitar la característica o para evitar la interrupción del servicio a la función.
-   En la actualización de servicio mensual, Microsoft proporciona información sobre nuevas características, nuevas funciones y mejoras en las características existentes. Por lo general, Microsoft implementa las actualizaciones del servicio a mediados de cada mes. Las actualizaciones se describen en [Novedades de Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune.md)..
-   En caso de retirada del servicio de Intune, sería notificado con 12 meses de antelación.

## Elegir la solución de administración que más le conviene
Puede configurar Intune de diversas maneras para administrar y proteger los dispositivos móviles y los equipos de su empresa (en adelante los denominaremos **dispositivos** en este documento).

-   **Configuración de Intune independiente.** Utilice la consola de administración basada en Web de Intune para administrar los dispositivos de su organización. Intune se puede usar sin una infraestructura de TI local, aunque si se usa Intune con los servicios de dominio de Active Directory, pueden emplearse las cuentas de usuario de dominio que se administran con los servicios de dominio mediante Intune.

-   **Intune con System Center Configuration Manager.** Use la consola de administración de Configuration Manager para administrar los equipos y dispositivos móviles de su empresa. Esta configuración puede ayudarle a administrar todos los dispositivos de la organización a través de una única consola, la consola de administración de Configuration Manager. Configuration Manager admite grandes cantidades de dispositivos móviles, servidores y equipos. Para obtener más información, consulte [Administrar dispositivos móviles con Configuration Manager y Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=271118) en la [Biblioteca de documentación de System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx).  Si necesita más ayuda para decidir cuál es el enfoque adecuado para usted, consulte [Formas de llevar a cabo la movilidad empresarial](/intune/plan-design/ways-to-do-enterprise-mobility.md).

-   Administración de dispositivos móviles proporcionada por Office 365, tal como se describe en [Formas de llevar a cabo la movilidad empresarial](/intune/plan-design/ways-to-do-enterprise-mobility.md).

## Obtenga más información acerca de Intune
Use estos recursos para obtener más información acerca de Intune:

-   En el [Centro de confianza de Microsoft Intune](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/) se proporciona información sobre las prácticas de seguridad, privacidad y cumplimiento de Intune y se describen algunas certificaciones de Intune.

-   [Capacidades de administración de dispositivos móviles en Microsoft Intune](/intune/understand-explore/mobile-device-management-capabilities-in-microsoft-intune.md)

### Consulte también
[Microsoft Intune](https://docs.microsoft.com/intune/)
[Biblioteca de documentación de System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx)

[Novedades de Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->

