---
title: Resultados del ejemplo de llamada
ms.date: 09/05/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: 96582e48912bb591d869bbc4df179299e6459f1e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500947"
---
# <a name="results-of-calling-example"></a>Resultados del ejemplo de llamada

**Específicos de Microsoft**

## <a name="cdecl"></a>__cdecl

El nombre de función representativo C es `_MyFunc`.

![Convención de llamada CDECL](../cpp/media/vc37i01.gif "vc37I01") el **__cdecl** convención de llamada

## <a name="stdcall-and-thiscall"></a>__stdcall y thiscall

El nombre representativo C (**__stdcall**) es `_MyFunc@20`. El nombre representativo C++ es específica de la implementación.

![&#95;&#95;stdcall y convenciones de llamada thiscall](../cpp/media/vc37i02.gif "vc37I02") __stdcall y thiscall convenciones de llamada

## <a name="fastcall"></a>__fastcall

El nombre representativo C (**__fastcall**) es `@MyFunc@20`. El nombre representativo C++ es específica de la implementación.

![Para la convención de llamada &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03") la convención de llamada __fastcall

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ejemplo de llamada: Prototipo de función y llamada](../cpp/calling-example-function-prototype-and-call.md)