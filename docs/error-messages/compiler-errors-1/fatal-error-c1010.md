---
title: Error irrecuperable C1010 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1010
dev_langs:
- C++
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b2123118be2a8a382f6b718499c5af16f88d111
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1010"></a>Error irrecuperable C1010
final de archivo inesperado al buscar la directiva de encabezado precompilado. ¿Compruebe si olvidó agregar ' #include nombre ' a su origen?  
  
 Un archivo de inclusión especificado con [/Yu](../../build/reference/yu-use-precompiled-header-file.md) no aparece en el archivo de origen.  Esta opción está habilitada de forma predeterminada en la mayoría de los tipos de proyecto de Visual C++ y "stdafx.h" es el valor predeterminado incluye el archivo especificado por esta opción.  
  
 En el entorno de Visual Studio, utilice uno de los métodos siguientes para resolver este error:  
  
-   Si no se utilizan encabezados precompilados en su proyecto, establezca el **crear o utilizar encabezado precompilado** propiedad de archivos de código fuente **no utilizar encabezados precompilados**. Para establecer esta opción del compilador, siga estos pasos:  
  
    1.  En el panel Explorador de soluciones del proyecto, haga clic en el nombre del proyecto y, a continuación, haga clic en **propiedades**.  
  
    2.  En el panel izquierdo, haga clic en el **C/C++** carpeta.  
  
    3.  Haga clic en el **encabezados precompilados** nodo.  
  
    4.  En el panel derecho, haga clic en **crear o utilizar encabezado precompilado**y, a continuación, haga clic en **no utilizar encabezados precompilados**.  
  
-   Asegúrese de que no accidentalmente han eliminado, cambiar o quitar el archivo de encabezado (de forma predeterminada, stdafx.h) del proyecto actual. Este archivo también debe incluirse antes que cualquier otro código en los archivos de origen con **#include "stdafx.h"**. (Este archivo de encabezado se especifica como **crear o utilizar encabezado Precompilado a través del archivo** propiedad del proyecto)