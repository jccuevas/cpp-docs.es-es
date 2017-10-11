---
title: Error irrecuperable C1128 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1128
dev_langs:
- C++
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 83ec855a3280b1169ce3537ecf85944939449316
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1128"></a>Error irrecuperable C1128
el número de secciones superó el límite de formato de archivo de objeto: compile con /bigobj  
  
 Un archivo .obj supera el número de secciones permitidas; ésta es una limitación del formato de archivo objeto COFF.  
  
 Esta limitación puede ser el resultado del uso de [/Gy](../../build/reference/gy-enable-function-level-linking.md) y una versión de depuración; **/Gy** hace que las funciones ir a sus propias secciones COMDAT. En una versión de depuración, hay una sección de información de depuración para cada función COMDAT.  
  
 También puede producirse el error C1128 cuando hay demasiadas funciones inline.  
  
 Para corregir este error, divida el archivo de código fuente en varios archivos de código fuente, compile sin **/Gy**, o compilar con [/bigobj (aumentar el número de secciones en. Archivo de obj)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Si no compila con **/Gy**, debe especificar las optimizaciones de forma individual, ya que **/O2** y **/O1** implican **/Gy**.  
  
 Si es posible, compile sin información de depuración.  
  
 También es posible que necesite disponer de creaciones de instancias de plantillas específicas en archivos de código fuente independientes, en lugar de esperar a que el compilador las emita.  
  
 Al trasladar código, C1128 probablemente aparecerán primero cuando se usa el x64 compilador y mucho más adelante con la x86 compilador. x64 tendrá al menos 4 secciones asociadas con cada función compilada **/Gy** o alineada a partir de plantillas o de clase inline: código, pdata e información de depuración.  x86 no tendrá pdata.
