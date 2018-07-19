---
title: Compilador advertencia (nivel 1) C4727 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4727
dev_langs:
- C++
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c92e42fe275f821e333a0f04a116034a5bb849a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282787"
---
# <a name="compiler-warning-level-1-c4727"></a>Advertencia del compilador (nivel 1) C4727
"PCH denominado archivo_pch con la misma marca de tiempo en archivo_obj_1 y archivo_obj_2.  Uso de primer PCH.  
  
 El error C4727 se produce cuando se compilan varios elementos con **/Yc**, y donde el compilador ha podido marcar todos los archivos .obj con la misma marca de tiempo de pch.  
  
 Para resolver, compilar un archivo de código fuente con **/Yc /c** (crea pch), y los demás compilan por separado con **/Yu /c** (utiliza pch), luego vincularlas juntos.  
  
 Por lo tanto, si se hiciera lo siguiente y se genera C4727:  
  
 **cl /clr/GL a.cpp b.cpp c.cpp /Ycstdafx.h**  
  
 En su lugar se haría lo siguiente:  
  
 **cl /clr/GL a.cpp /Ycstdafx.h /c**  
  
 **cl /clr/GL b.cpp c.cpp /Yustdafx.h /link a.obj**  
  
 Para obtener más información, consulte  
  
-   [/Yc (Crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [/Yu (Usar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md)