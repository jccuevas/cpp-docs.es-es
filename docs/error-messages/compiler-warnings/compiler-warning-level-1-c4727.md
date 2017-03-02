---
title: Error de compilador (nivel 1) de advertencia C4727 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4727
dev_langs:
- C++
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c3d77b053fb866a16e6642ba2e6a24ff6d85798f
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4727"></a>Advertencia del compilador (nivel 1) C4727
"PCH denominado archivo_pch con la misma marca de tiempo en archivo_obj_1 y archivo_obj_2.  Uso de primer PCH.  
  
 El error C4727 se produce cuando se compilan varios elementos con **/Yc**, y donde el compilador pudo marcar todos los archivos .obj con la misma marca de tiempo de pch.  
  
 Para resolver, compilar un archivo de código fuente con **/Yc /c** (crea pch), y los demás compilan por separado con **/Yu /c** (utiliza pch), a continuación, vincularlos.  
  
 Por lo tanto, si hiciera lo siguiente y se genera C4727:  
  
 **cl /clr/GL a.cpp b.cpp c.cpp /Ycstdafx.h**  
  
 En su lugar debe hacer lo siguiente:  
  
 **cl /clr/GL a.cpp /Ycstdafx.h /c**  
  
 **cl /clr/GL b.cpp c.cpp /Yustdafx.h /link a.obj**  
  
 Para obtener más información, consulte  
  
-   [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [/Yu (utilizar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md)
