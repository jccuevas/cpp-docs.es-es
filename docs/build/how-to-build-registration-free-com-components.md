---
title: "Cómo: crear componentes COM sin registro | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bba711f88a53a3d9b6f9eae1faed09670e95d497
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-build-registration-free-com-components"></a>Cómo: Crear componentes COM de registro gratuito
Los componentes COM sin registro son componentes COM que tienen los manifiestos integrados en los archivos DLL.  
  
### <a name="to-build-manifests-into-com-components"></a>Para generar manifiestos en los componentes COM  
  
1.  Abra las páginas de propiedades de proyecto para el componente COM.  
  
2.  Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **herramienta manifiesto** nodo.  
  
3.  Seleccione el **de entrada y salida** página de propiedades y, después, establezca el **incrustar manifiesto** propiedad **Sí**.  
  
4.  Haga clic en **Aceptar**.  
  
5.  Compile la solución.  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones aisladas](http://msdn.microsoft.com/library/aa375190)   
 [Acerca de los ensamblados en paralelo](http://msdn.microsoft.com/library/ff951640)   
 [Procedimiento para compilar aplicaciones aisladas que empleen componentes COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)