---
title: Extensiones de Microsoft
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: a2d0846e55122f177b4868c2e80c4f1d27267f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179411"
---
# <a name="microsoft-extensions"></a>Extensiones de Microsoft

*ASM-instrucción*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm***instrucción de ensamblado* **;** <sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm {** *Assembly-Instruction-List* **};** <sub>OPT</sub>

*Assembly-Instruction-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrucción de ensamblado* **;** <sub>OPT</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp; *-instruction* **;** *Assembly-Instruction-List* **;** <sub>OPT</sub>

*MS-Modifier-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*MS-modificador* *MS-Modifier-List*<sub>OPC</sub>

*modificador MS*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__syscall** (reservado para implementaciones futuras)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__oldcall** (reservado para implementaciones futuras)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__unaligned** (reservado para implementaciones futuras)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *-modificador*

*based-modificador*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__based (** *tipo basado en* **)**

*tipo basado*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nombre*
