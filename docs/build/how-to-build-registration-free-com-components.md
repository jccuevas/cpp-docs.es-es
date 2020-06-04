---
title: Procedimiento Compilar componentes COM sin registro
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188943"
---
# <a name="how-to-build-registration-free-com-components"></a>Procedimiento Compilar componentes COM sin registro

Los componentes COM sin registro son aquellos que tienen manifiestos integrados en los archivos DLL.

### <a name="to-build-manifests-into-com-components"></a>Para compilar manifiestos en componentes COM

1. Abra las páginas de propiedades del proyecto para el componente COM.

1. Expanda el nodo **Propiedades de configuración** y, después, expanda el nodo **Herramienta Manifiesto**.

1. Seleccione la página de propiedades **Entrada y salida** y, luego, establezca la propiedad **Incrustar manifiesto** igual a **Sí**.

1. Haga clic en **Aceptar**.

1. Compile la solución.

## <a name="see-also"></a>Vea también

[Cómo: Compilar aplicaciones aisladas que empleen componentes COM](how-to-build-isolated-applications-to-consume-com-components.md)
