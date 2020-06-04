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
ms.openlocfilehash: edbeb187e568b833673d91ef70ff57fbd460659c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179060"
---
# <a name="results-of-calling-example"></a>Resultados del ejemplo de llamada

**Específicos de Microsoft**

## <a name="__cdecl"></a>__cdecl

El nombre de función representativo de C es `_MyFunc`.

![Convención de llamada CDECL](../cpp/media/vc37i01.gif "Convención de llamada CDECL") <br/>
La Convención de llamada de **__cdecl**

## <a name="__stdcall-and-thiscall"></a>__stdcall y thiscall

El nombre representativo de C ( **__stdcall**) es `_MyFunc@20`. El C++ nombre representativo es específico de la implementación.

![&#95;&#95;convenciones de llamada Stdcall y thiscall](../cpp/media/vc37i02.gif "&#95;&#95;convenciones de llamada Stdcall y thiscall") <br/>
Las convenciones de llamada de __stdcall y thiscall

## <a name="__fastcall"></a>__fastcall

El nombre representativo de C ( **__fastcall**) es `@MyFunc@20`. El C++ nombre representativo es específico de la implementación.

![Convención de llamada &#95; &#95;para fastcall](../cpp/media/vc37i03.gif "Convención de llamada &#95; &#95;para fastcall") <br/>
La convención de llamada __fastcall

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Ejemplo de llamada: Prototipo de función y llamada](../cpp/calling-example-function-prototype-and-call.md)
