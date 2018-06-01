---
title: Error del compilador C2393 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2393
dev_langs:
- C++
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 057537c8efcf6e827d9ac9aaf36c0eace6d24156
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704035"
---
# <a name="compiler-error-c2393"></a>Error del compilador C2393

> '*símbolo*': símbolo por appdomain no se puede asignar en el segmento '*segmento*'

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

El uso de [appdomain](../../cpp/appdomain.md) variables implica que se está compilando con **/CLR: pure** o **/CLR: safe**, y una imagen pura o segura no puede contener segmentos de datos.

Vea [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2393. Para corregir este problema, no cree un segmento de datos.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```