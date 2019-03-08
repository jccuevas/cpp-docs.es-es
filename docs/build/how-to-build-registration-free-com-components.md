---
title: Procedimiento Compilar componentes COM sin registro
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 503c3e4399359d793ce660f36844d2edc6602146
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416779"
---
# <a name="how-to-build-registration-free-com-components"></a>Procedimiento Compilar componentes COM sin registro

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
[Cómo: Compilar aplicaciones aisladas que empleen componentes COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)
