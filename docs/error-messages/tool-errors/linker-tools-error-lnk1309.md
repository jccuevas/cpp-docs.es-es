---
title: Las herramientas del vinculador LNK1309 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1309
dev_langs: C++
helpviewer_keywords: LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: febaeeeabdf045ee7d223b7514d63202ded1e99c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1309"></a>Error de las herramientas del vinculador LNK1309
módulo tipo1 detectado; no válido con el modificador/CLRIMAGETYPE: tipo2  
  
 Se solicitó un tipo de imagen CLR con **/CLRIMAGETYPE** pero el vinculador no puede crear una imagen de ese tipo porque uno o varios módulos no eran compatibles con ese tipo.  
  
 Por ejemplo, verá LNK1309 si especifica **/CLRIMAGETYPE:safe** y pasar un módulo compilado con **/CLR: pure**.  
  
 También verá LNK1309 si intentan volver a compilar una aplicación pura CLR confianza parcial mediante .lib ptrustu [d]. Para obtener información sobre cómo crear una aplicación de confianza parcial, vea [Cómo: crear una aplicación de confianza parcial mediante quitando la dependencia en la DLL de biblioteca de CRT](../../dotnet/create-a-partially-trusted-application.md).  
  
 Para obtener más información, consulte [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) y [/CLRIMAGETYPE (Especificar tipo de imagen de CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).