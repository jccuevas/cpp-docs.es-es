---
title: Resultados del ejemplo de llamada
ms.date: 11/19/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: dcd1f9002362b7726883c6ce4f74fda9ab593544
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175423"
---
# <a name="results-of-calling-example"></a>Resultados del ejemplo de llamada

**Específicos de Microsoft**

## <a name="cdecl"></a>__cdecl

El nombre de función representativo C es `_MyFunc`.

![Convención de llamada CDECL](../cpp/media/vc37i01.gif "convención de llamada CDECL") <br/>
El **__cdecl** convención de llamada

## <a name="stdcall-and-thiscall"></a>__stdcall y thiscall

El nombre representativo C (**__stdcall**) es `_MyFunc@20`. El nombre representativo C++ es específica de la implementación.

![&#95;&#95;stdcall y convenciones de llamada thiscall](../cpp/media/vc37i02.gif "&#95;&#95;stdcall y convenciones de llamada thiscall") <br/>
Las convenciones de llamada de __stdcall y thiscall

## <a name="fastcall"></a>__fastcall

El nombre representativo C (**__fastcall**) es `@MyFunc@20`. El nombre representativo C++ es específica de la implementación.

![Para la convención de llamada &#95; &#95;fastcall](../cpp/media/vc37i03.gif "para la convención de llamada &#95; &#95;fastcall") <br/>
La convención de llamada __fastcall

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ejemplo de llamada: Prototipo de función y llamada](../cpp/calling-example-function-prototype-and-call.md)