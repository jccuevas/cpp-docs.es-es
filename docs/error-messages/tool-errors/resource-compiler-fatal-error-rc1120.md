---
title: Error irrecuperable del compilador de recursos RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: 855a76ff63145695a7063944701d7acc684e0084
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173015"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Error irrecuperable del compilador de recursos RC1120

memoria insuficiente, número necesario de bytes

El compilador de recursos se quedó sin almacenamiento para los elementos que almacena en su montón. Normalmente, este es el resultado de tener demasiados símbolos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Aumente el espacio del archivo de intercambio de Windows. Para obtener más información sobre cómo aumentar el espacio de archivo de intercambio, consulte memoria virtual en la ayuda de Windows.

1. Elimine los archivos de inclusión innecesarios, especialmente los `#define`s y los prototipos de función innecesarios.

1. Divida el archivo actual en dos o más archivos y compílelo por separado.

1. Quitar otros programas o controladores que se ejecutan en el sistema, lo que podría estar consumiendo grandes cantidades de memoria.
