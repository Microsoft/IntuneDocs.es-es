---
title: Retirar un PC de Windows | Microsoft Intune
description: "Cómo retirar un PC de Windows administrado por Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 19e8e2b6a7eaa3cf02e4296a6fd147baa1472b61


---

# <a name="retire-a-windows-pc"></a>Retirar un PC de Windows
Utilice los pasos siguientes para retirar los PC que se administran mediante Intune.

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** (u otro grupo que contenga el equipo que quiera retirar).

2.  Seleccione los dispositivos que quiera retirar y, después, elija **Retirar/Eliminar datos**.

Para volver a inscribir un equipo en Intune, vuelva a instalar el cliente de software en el equipo según lo que se indica en [Instalar el cliente de equipos Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Si un equipo no se puede conectar a Intune, verá un mensaje en el área de trabajo **Panel**.

Cuando retira un equipo:

-   Se quita del inventario y la administración de Intune y la licencia asociada al equipo queda disponible para poder reutilizarla. La opción de retirar o borrar un equipo quita el cliente del software de Intune, pero no elimina las aplicaciones o los datos del equipo. Esta retirada no efectúa un borrado completo en el equipo.

-   Su estado deja de aparecer en la consola de Intune.

-   Intune quita el cliente de software del equipo. Si el equipo no está conectado al servicio de Intune, el cliente de software se quitará la próxima vez que se conecte.

-   Microsoft Intune Endpoint Protection se quita del equipo. Si el equipo tiene instalada otra aplicación de extremos que está deshabilitada, esa aplicación se puede volver a habilitar después de quitar Microsoft Intune Endpoint Protection y, así, garantizar la protección del equipo.

-   Se quitan las directivas del equipo y se cambian los valores establecidos por las directivas.

-   El equipo deja de recibir actualizaciones de software o de definiciones de malware procedentes del servicio de Intune.

-   Según como estén configurados, los equipos retirados pueden seguir recibiendo actualizaciones mediante Windows Server Update Services, Windows Update o Microsoft Update.

    > [!IMPORTANT]
    > Si el software cliente se instaló con un objeto de directiva de grupo (GPO), debe quitar dicho objeto para poder quitar el software cliente, a fin de evitar que el software se reinstale.

    Si el cliente no se puede desinstalar, lea [Solucionar problemas de Endpoint Protection en Microsoft Intune](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) para obtener más ayuda.

### <a name="see-also"></a>Consulte también

[Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->

