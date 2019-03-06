---
title: Filtrar Compilar aplicaciones aisladas que empleen componentes COM
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 01b5c7056bd10a7c1f88df74b5c6b4aa78ff3fde
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417884"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Procedimiento Compilar aplicaciones aisladas que empleen componentes COM

Aplicaciones aisladas son aplicaciones que tienen manifiestos integrados en el programa. Puede crear aplicaciones aisladas que empleen componentes COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Para agregar referencias COM a manifiestos de aplicaciones aisladas

1. Abra las páginas de propiedades de proyecto para la aplicación aislada.

1. Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **herramienta manifiesto** nodo.

1. Seleccione el **COM aislado** página de propiedades y, después, establezca el **nombre de archivo del componente** propiedad en el nombre del componente COM que desea que la aplicación aislada para consumir.

1. Haga clic en **Aceptar**.

### <a name="to-build-manifests-into-isolated-applications"></a>Para generar los manifiestos en aplicaciones aisladas

1. Abra las páginas de propiedades de proyecto para la aplicación aislada.

1. Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **herramienta manifiesto** nodo.

1. Seleccione el **de entrada y salida** página de propiedades y, después, establezca el **incrustar manifiesto** propiedad igual a **Sí**.

1. Haga clic en **Aceptar**.

1. Compile la solución.

## <a name="see-also"></a>Vea también

[Aplicaciones aisladas](/windows/desktop/SbsCs/isolated-applications)<br/>
[Acerca de los ensamblados en paralelo](/windows/desktop/SbsCs/about-side-by-side-assemblies-)
