---
title: 'Cómo: Crear componentes COM de registro gratuito'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 4f4ebf121b761c37969fa3f9788bda52d913f340
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463536"
---
# <a name="how-to-build-registration-free-com-components"></a>Cómo: Crear componentes COM de registro gratuito

Los componentes COM sin registro son componentes COM que tienen manifiestos integrados en los archivos DLL.

### <a name="to-build-manifests-into-com-components"></a>Para generar los manifiestos en componentes COM

1. Abra las páginas de propiedades de proyecto para el componente COM.

1. Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **herramienta manifiesto** nodo.

1. Seleccione el **de entrada y salida** página de propiedades y, después, establezca el **incrustar manifiesto** propiedad igual a **Sí**.

1. Haga clic en **Aceptar**.

1. Compile la solución.

## <a name="see-also"></a>Vea también

[Aplicaciones aisladas](/windows/desktop/SbsCs/isolated-applications)<br/>
[Acerca de los ensamblados en paralelo](/windows/desktop/SbsCs/about-side-by-side-assemblies-)<br/>
[Procedimiento para compilar aplicaciones aisladas que empleen componentes COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)