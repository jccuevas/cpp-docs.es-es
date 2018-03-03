---
title: "Cómo: compilar aplicaciones aisladas que utilicen componentes COM | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aaeef56f122d10f983313ab1c839db40f4e92aa4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Cómo: Compilar aplicaciones aisladas que utilicen componentes COM
Aplicaciones aisladas son aquéllas que tienen manifiestos integrados en el programa. Puede crear aplicaciones aisladas que utilicen componentes COM.  
  
### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Para agregar referencias COM a manifiestos de aplicaciones aisladas  
  
1.  Abra las páginas de propiedades de proyecto para la aplicación aislada.  
  
2.  Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **herramienta manifiesto** nodo.  
  
3.  Seleccione el **COM aislado** página de propiedades y, después, establezca el **nombre de archivo del componente** propiedad en el nombre del componente COM que desea que la aplicación aislada para consumir.  
  
4.  Haga clic en **Aceptar**.  
  
### <a name="to-build-manifests-into-isolated-applications"></a>Para generar manifiestos en aplicaciones aisladas  
  
1.  Abra las páginas de propiedades de proyecto para la aplicación aislada.  
  
2.  Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **herramienta manifiesto** nodo.  
  
3.  Seleccione el **de entrada y salida** página de propiedades y, después, establezca el **incrustar manifiesto** propiedad **Sí**.  
  
4.  Haga clic en **Aceptar**.  
  
5.  Compile la solución.  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones aisladas](http://msdn.microsoft.com/library/aa375190)   
 [Acerca de los ensamblados en paralelo](http://msdn.microsoft.com/library/ff951640)