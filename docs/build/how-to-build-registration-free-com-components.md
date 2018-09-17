---
title: 'Cómo: compilar componentes COM sin registro | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0a9e1769ff0ba9a0589f9d59c3d1f1ed2fc5bcb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699860"
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