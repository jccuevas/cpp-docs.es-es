---
title: Error irrecuperable del compilador de recursos RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: eff46ddee118c3355e548c73220b407db0561e36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374264"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Error irrecuperable del compilador de recursos RC1120

memoria insuficiente, necesita el número de bytes

El compilador de recursos se quedó sin almacenamiento para los elementos que almacena en su montón. Normalmente es el resultado de tener demasiados símbolos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Aumente el espacio de archivo de intercambio de Windows. Para obtener más información sobre cómo aumentar el espacio de archivo de intercambio, consulte la memoria virtual en la Ayuda de Windows.

1. Elimine los archivos de inclusión, especialmente que `#define`y función de los prototipos.

1. Divida el archivo actual en dos o más archivos y compílelos por separado.

1. Quitar otros programas o controladores que se ejecutan en el sistema, que podría estar consumiendo una cantidad significativa de memoria.