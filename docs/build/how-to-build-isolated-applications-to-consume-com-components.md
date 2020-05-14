---
title: Procedimiento para compilar aplicaciones aisladas que empleen componentes COM
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 8ae3c51502267f202cbb85ea7be2a81dc3310410
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493232"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Procedimiento para compilar aplicaciones aisladas que empleen componentes COM

Las aplicaciones aisladas son aquellas que tienen manifiestos integrados en el programa. Puede crear aplicaciones aisladas para emplear componentes COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Para agregar referencias COM a manifiestos de aplicaciones aisladas

1. Abra las páginas de propiedades del proyecto para aplicación aislada.

1. Expanda el nodo **Propiedades de configuración** y, después, expanda el nodo **Herramienta Manifiesto**.

1. Seleccione la página de propiedades **COM aislado** y establezca la propiedad **Nombre de archivo de componente** en el nombre del componente COM que quiera que use la aplicación aislada.

1. Haga clic en **Aceptar**.

### <a name="to-build-manifests-into-isolated-applications"></a>Para compilar manifiestos en aplicaciones aisladas

1. Abra las páginas de propiedades del proyecto para aplicación aislada.

1. Expanda el nodo **Propiedades de configuración** y, después, expanda el nodo **Herramienta Manifiesto**.

1. Seleccione la página de propiedades **Entrada y salida** y, luego, establezca la propiedad **Incrustar manifiesto** igual a **Sí**.

1. Haga clic en **Aceptar**.

1. Compile la solución.

## <a name="see-also"></a>Vea también

[Aplicaciones aisladas](/windows/win32/SbsCs/isolated-applications)<br/>
[Acerca de los ensamblados en paralelo](/windows/win32/SbsCs/about-side-by-side-assemblies-)
