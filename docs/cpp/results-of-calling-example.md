---
title: Resultados del ejemplo de llamada | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5687adfada8657ae26edd9001db8990ff08864e9
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894702"
---
# <a name="results-of-calling-example"></a>Resultados del ejemplo de llamada

**Específicos de Microsoft**

## <a name="cdecl"></a>__cdecl
El nombre de función representativo C es `_MyFunc`.

![Convención de llamada CDECL](../cpp/media/vc37i01.gif "vc37I01")  
El **__cdecl** convención de llamada

## <a name="stdcall-and-thiscall"></a>__stdcall y thiscall

El nombre representativo C (**__stdcall**) es `_MyFunc@20`. El nombre representativo C++ es específica de la implementación.

![&#95;&#95;stdcall y convenciones de llamada thiscall](../cpp/media/vc37i02.gif "vc37I02")  
Las convenciones de llamada de __stdcall y thiscall

## <a name="fastcall"></a>__fastcall

El nombre representativo C (**__fastcall**) es `@MyFunc@20`. El nombre representativo C++ es específica de la implementación.

![Para la convención de llamada &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03")  
La convención de llamada __fastcall

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ejemplo de llamada: Prototipo de función y llamada](../cpp/calling-example-function-prototype-and-call.md)