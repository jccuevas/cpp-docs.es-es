---
title: Redistribuir aplicaciones cliente Web | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e764e42cb558d2e13e0609cb139e9538a72d09ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-web-client-applications"></a>Redistribuir aplicaciones cliente web
Si su aplicación utiliza las clases MFC que implementan el control WebBrowser (por ejemplo, `CHtmlView` o `CHtmlEditView`), Microsoft Internet Explorer 4.0 o posterior debe al menos mínimamente instalarse en el equipo de destino.  
  
 Instalar la versión más reciente de Internet Explorer también garantiza que el equipo de destino tiene los archivos de control comunes más recientes.  
  
 Información acerca de cómo instalar componentes mínimos de Internet Explorer está disponible en el siguiente artículo de Knowledge Base:  
  
-   Q185375, HOWTO: Crear una instalación única EXE de Internet Explorer ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))  
  
 Encontrará artículos de Knowledge Base en MSDN Library o en [http://support.microsoft.com](http://support.microsoft.com).  
  
## <a name="see-also"></a>Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)