---
title: Las extensiones de Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5699ce82a6e8537f12da50fdcb8288da167ecca3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752244"
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