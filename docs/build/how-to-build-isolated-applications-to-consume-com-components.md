---
title: 'Cómo: compilar aplicaciones aisladas que empleen componentes COM | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b94a41aef1122a507a8966c475b9a87c69e3789
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196837"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Cómo: Compilar aplicaciones aisladas que utilicen componentes COM
Aplicaciones aisladas son aplicaciones que tienen manifiestos integrados en el programa. Puede crear aplicaciones aisladas que empleen componentes COM.  
  
### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Para agregar referencias COM a manifiestos de aplicaciones aisladas  
  
1.  Abra las páginas de propiedades de proyecto para la aplicación aislada.  
  
2.  Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **herramienta manifiesto** nodo.  
  
3.  Seleccione el **COM aislado** página de propiedades y, después, establezca el **nombre de archivo del componente** propiedad en el nombre del componente COM que desea que la aplicación aislada para consumir.  
  
4.  Haga clic en **Aceptar**.  
  
### <a name="to-build-manifests-into-isolated-applications"></a>Para generar los manifiestos en aplicaciones aisladas  
  
1.  Abra las páginas de propiedades de proyecto para la aplicación aislada.  
  
2.  Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **herramienta manifiesto** nodo.  
  
3.  Seleccione el **de entrada y salida** página de propiedades y, después, establezca el **incrustar manifiesto** propiedad igual a **Sí**.  
  
4.  Haga clic en **Aceptar**.  
  
5.  Compile la solución.  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones aisladas](/windows/desktop/SbsCs/isolated-applications)   
 [Acerca de los ensamblados en paralelo](/windows/desktop/SbsCs/about-side-by-side-assemblies-)