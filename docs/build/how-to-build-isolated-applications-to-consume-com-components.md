---
title: Procedimiento Crear aplicaciones aisladas para consumir componentes COM
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 8ae3c51502267f202cbb85ea7be2a81dc3310410
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493232"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Procedimiento Crear aplicaciones aisladas para consumir componentes COM

Las aplicaciones aisladas son aplicaciones que tienen manifiestos integrados en el programa. Puede crear aplicaciones aisladas para consumir componentes COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Para agregar referencias COM a manifiestos de aplicaciones aisladas

1. Abra las páginas de propiedades del proyecto para la aplicación aislada.

1. Expanda el nodo **propiedades de configuración** y, a continuación, expanda el nodo **herramienta de manifiesto** .

1. Seleccione la página de propiedades **com aislada** y, a continuación, establezca la propiedad **nombre de archivo de componente** en el nombre del componente com que desea que utilice la aplicación aislada.

1. Haga clic en **OK**.

### <a name="to-build-manifests-into-isolated-applications"></a>Para compilar manifiestos en aplicaciones aisladas

1. Abra las páginas de propiedades del proyecto para la aplicación aislada.

1. Expanda el nodo **propiedades de configuración** y, a continuación, expanda el nodo **herramienta de manifiesto** .

1. Seleccione la página de propiedades **entrada y salida** y, a continuación, establezca la propiedad **incrustar manifiesto** en **sí**.

1. Haga clic en **OK**.

1. Compile la solución.

## <a name="see-also"></a>Vea también

[Aplicaciones aisladas](/windows/win32/SbsCs/isolated-applications)<br/>
[Acerca de los ensamblados en paralelo](/windows/win32/SbsCs/about-side-by-side-assemblies-)
