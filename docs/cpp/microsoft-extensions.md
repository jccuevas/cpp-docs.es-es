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
ms.openlocfilehash: 70b1e0e6ef1294ff23952816db6f468022609f4f
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408380"
---
# <a name="microsoft-extensions"></a>Extensiones de Microsoft
*instrucción de ASM*:  
 **__asm***instrucción de ensamblado* **;** participar    
  
 **__asm {***lista de instrucciones de ensamblado***};** participar      
  
 *lista de instrucciones de ensamblado*:  
 *instrucción de ensamblado* **;** participar  
  
 *instrucción de ensamblado* **;** *lista de instrucciones de ensamblado* **;** participar  
  
 *modificador-MS-list*:  
 *modificador de MS-ms-modificador-list*participar  
  
 *MS-modifier*:  
 **__cdecl**  
  
 **__fastcall**  
  
 **__stdcall**  
  
 **__syscall** (reservado para implementaciones futuras)  
  
 **__oldcall** (reservado para implementaciones futuras)  
  
 **__unaligned** (reservado para implementaciones futuras)  
  
 *en función de modificador*  
  
 *en función de modificador*:  
 **__based (** *en función de tipo* **)**  
  
 *en función de tipo*:  
 *name*  