---
title: Extensiones de Microsoft
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: d8104c2df2335e11dcb711108d566e0fdd069762
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592210"
---
# <a name="microsoft-extensions"></a>Extensiones de Microsoft

*instrucción de ASM*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm***instrucción de ensamblado* **;** <sub>participar  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {***lista de instrucciones de ensamblado***};** <sub>participar    </sub>

*lista de instrucciones de ensamblado*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de ensamblado* **;** <sub>participar</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de ensamblado* **;** *lista de instrucciones de ensamblado* **;** <sub>participar</sub>

*modificador-MS-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*MS-modifier* *modificador-ms-list*<sub>participar</sub>

*MS-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** (reservado para implementaciones futuras)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** (reservado para implementaciones futuras)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** (reservado para implementaciones futuras)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*en función de modificador*

*en función de modificador*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *en función de tipo* **)**

*en función de tipo*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Nombre*