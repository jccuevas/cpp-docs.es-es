---
title: "Ejecutar la automatización remota mediante AUTOCLIK y AUTODRIV | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- AUTOCLIK sample [MFC]
ms.assetid: 8900c0de-8dba-4f0a-8d9e-7db77a1f4f46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 791655047eaf07732e1e006e8cc3ea8e7dec4727
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="running-remote-automation-using-autoclik-and-autodriv"></a>Ejecutar la automatización remota mediante AUTOCLIK y AUTODRIV
AUTOCLIK es una sencilla aplicación de ejemplo de servidor de automatización que puede utilizar como base desde la que se va a obtener más información acerca de la automatización remota. AUTODRIV es una sencilla aplicación de cliente de automatización que controla AUTOCLIK. Puede utilizarlos para demostrar la automatización remota.  
  
#### <a name="to-install-autoclikexe-on-two-machines-and-drive-it-using-remote-automation"></a>Para instalar AUTOCLIK. Archivo EXE en dos equipos y ejecutarla mediante automatización remota  
  
1.  Instalar el [AUTOCLIK](../visual-cpp-samples.md) ejemplo de aplicación en el equipo de desarrollo.  
  
2.  Genere AUTOCLIK. EXE.  
  
3.  Ejecute la aplicación AUTOCLIK. EXE en independiente forma y, a continuación, apague. Así registrará como un servidor de automatización.  
  
4.  Copie la aplicación AUTOCLIK. EXE en un equipo remoto, ejecutarlo en él y, a continuación, apague.  
  
5.  Ejecute AUTODRIV. Archivo EXE en el equipo local del equipo y compruebe que se ejecuta inicia AUTOCLIK. EXE. Para obtener más información sobre AUTODRIV. EXE, consulte [AUTOCLIK](../visual-cpp-samples.md).  
  
6.  En el equipo remoto, inicie AUTMGR32. EXE (Administrador de automatización).  
  
7.  En el equipo remoto, inicie RACMGR32. EXE (Administrador de conexiones de automatización remota).  
  
8.  En el Administrador de conexiones de automatización remota, seleccione AutoClik.Document en la **clases OLE** lista.  
  
9. Elija una directiva de seguridad del sistema desde la **acceso de cliente** tab para conceder acceso de cliente a AutoClik.Document.  
  
10. En el equipo local, inicie RACMGR32. EXE y seleccione AutoClik.Document en la **clases OLE** lista.  
  
11. Desde el **conexión del servidor** ficha, elija la dirección de red del equipo remoto y el protocolo de red adecuado.  
  
12. Con aún AutoClik.Document seleccionado en el **clases OLE** cuadro de lista, elija la **remoto** línea de comandos desde el `Register` menú.  
  
13. En el equipo local, ejecute AUTODRIV. EXE o el equivalente AUTOCLIK. Proyecto de Visual Basic de MAK si desea tener un de Visual Basic, en lugar de MFC, cliente.  
  
 En el equipo remoto, ahora podrá ver AUTOCLIK ejecutar comandos iniciadas desde el cliente local.  
  
## <a name="see-also"></a>Vea también  
 [Automatización remota](../mfc/remote-automation.md)

