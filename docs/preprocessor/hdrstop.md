---
title: hdrstop | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
dev_langs: C++
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf1bd1d80f692695c1cbf4ad535d2c5e759e4ea5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hdrstop"></a>hdrstop
Proporciona control adicional sobre los nombres de archivo de la precompilación y sobre la ubicación en la que se guarda el estado de la compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma hdrstop [( "filename" )]    
```  
  
## <a name="remarks"></a>Comentarios  
 El *filename* es el nombre del archivo de encabezado precompilado para utilizar o crear (dependiendo de si [/Yu](../build/reference/yu-use-precompiled-header-file.md) o [/Yc](../build/reference/yc-create-precompiled-header-file.md) se especifica). Si *filename* no contiene una especificación de ruta de acceso, se presupone que el archivo de encabezado precompilado en el mismo directorio que el archivo de origen.  
  
 Si un archivo de C o C++ contiene una **hdrstop** pragma cuando se compila con/Yc, el compilador guarda el estado de la compilación hasta la ubicación de la directiva pragma. El estado compilado del código que aparece detrás de la instrucción pragma no se guarda.  
  
 Use *filename* un nombre al archivo de encabezado precompilado en el que se guarda el estado compilado. Un espacio entre **hdrstop** y *filename* es opcional. El nombre de archivo especificado en el **hdrstop** pragma es una cadena y, por tanto, está sujeto a las restricciones de cualquier cadena de C o C++. En concreto, debe incluirse entre comillas y usar el carácter de escape (la barra diagonal inversa) para especificar nombres de directorio. Por ejemplo:  
  
```  
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )  
```  
  
 El nombre del archivo de encabezado precompilado se determina según las reglas siguientes, en orden de prioridad:  
  
1.  El argumento de la opción del compilador /Fp  
  
2.  El *filename* argumento #**pragma hdrstop**  
  
3.  El nombre base del archivo de código fuente con una extensión .PCH  
  
 Para las opciones /Yc e /Yu, si ninguna de las opciones de dos compilación ni la **hdrstop** pragma especifica un nombre de archivo, el nombre base del archivo de origen se utiliza como el nombre base del archivo de encabezado precompilado.  
  
 Puede usar también comandos de preprocesamiento para realizar la sustitución de macros del modo siguiente:  
  
```  
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"  
#define PCH_FNAME "PROG.PCH"  
.  
.  
.  
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )  
```  
  
 Las reglas siguientes determinan dónde el **hdrstop** se puede colocar la pragma:  
  
-   Debe aparecer fuera de cualquier declaración o definición de datos o función.  
  
-   Se debe especificar en el archivo de código fuente, no en un archivo de encabezado.  
  
## <a name="example"></a>Ejemplo  
  
```  
#include <windows.h>                 // Include several files  
#include "myhdr.h"  
  
__inline Disp( char *szToDisplay )   // Define an inline function  
{  
    ...                              // Some code to display string  
}  
#pragma hdrstop  
```  
  
 En este ejemplo, el **hdrstop** pragma aparece después de que se han incluido dos archivos y se ha definido una función insertada. Esto podría parecer, a primera vista, una colocación extraña de una instrucción pragma. Tenga en cuenta, sin embargo, que el uso las opciones de precompilación manual, /Yc y/Yu, con el **hdrstop** pragma permite precompilar archivos de código fuente, incluido el código insertado. El compilador de Microsoft no le limita a precompilar solo las declaraciones de datos.  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)