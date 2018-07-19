---
title: Error irrecuperable C1128 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1128
dev_langs:
- C++
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d2604b17b656efab3a3575469eff6a02df960c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226270"
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