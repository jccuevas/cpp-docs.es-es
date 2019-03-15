---
title: Procedimiento Compilar componentes COM sin registro
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809605"
---
# <a name="how-to-build-registration-free-com-components"></a>Filtrar Compilar componentes COM sin registro

Los componentes COM sin registro son componentes COM que tienen manifiestos integrados en los archivos DLL.

### <a name="to-build-manifests-into-com-components"></a>Para generar los manifiestos en componentes COM

1. Abra las páginas de propiedades de proyecto para el componente COM.

1. Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **herramienta manifiesto** nodo.

1. Seleccione el **de entrada y salida** página de propiedades y, después, establezca el **incrustar manifiesto** propiedad igual a **Sí**.

1. Haga clic en **Aceptar**.

1. Compile la solución.

## <a name="see-also"></a>Vea también

[Cómo: Compilar aplicaciones aisladas que empleen componentes COM](how-to-build-isolated-applications-to-consume-com-components.md)
