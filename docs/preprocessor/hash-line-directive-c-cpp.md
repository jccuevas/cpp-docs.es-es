---
title: "#line (Directiva) (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#line"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#line (directiva)"
  - "directiva de línea (#line)"
  - "preprocesador, directivas"
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #line (Directiva) (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La directiva `#line` indica al preprocesador que cambie el número de línea y el nombre de archivo almacenados internamente por el compilador a un número de línea y un nombre de archivo especificados.  
  
## Sintaxis  
  
```  
  
#line   
digit-sequence ["filename"]  
```  
  
## Comentarios  
 El compilador utiliza el número de línea y el nombre de archivo opcional para hacer referencia a los errores que encuentra durante la compilación.  El número de línea suele referirse a la línea de entrada actual, y el nombre de archivo hace referencia al archivo de entrada actual.  El número de línea se incrementa una vez que se procesa cada línea.  
  
 El valor de *digit\-sequence* puede ser cualquier constante de tipo entero.  El reemplazo de macros se pueden realizar en los tokens de preprocesamiento, pero el resultado debe evaluarse como la sintaxis correcta.  *filename* puede ser cualquier combinación de caracteres y se debe especificar entre comillas dobles \(**" "**\).  Si se omite *filename*, el nombre de archivo anterior permanece sin cambios.  
  
 Se puede cambiar el número de línea y el nombre de archivo de código fuente mediante una directiva `#line`.  El traductor utiliza el número de línea y el nombre de archivo para determinar los valores de las macros predefinidas **\_\_FILE\_\_** y **\_\_LINE\_\_**.  Estas macros se pueden utilizar para insertar mensajes de error autodescriptivos en el texto del programa.  Para obtener más información sobre estas macros predefinidas, vea [Macros predefinidas](../preprocessor/predefined-macros.md).  
  
 La macro **\_\_FILE\_\_** se expande a una cadena delimitada por comillas dobles \(**" "**\) cuyo contenido es el nombre de archivo.  
  
 Si se cambia el número de línea y el nombre de archivo, el compilador omite los valores anteriores y continúa el procesamiento con los nuevos valores.  Los generadores de programas suelen emplear la directiva `#line` para hacer que los mensajes de error hagan referencia al archivo de código fuente original en lugar de al programa generado.  
  
 En los ejemplos siguientes se muestran `#line` y las macros **\_\_LINE\_\_** y **\_\_FILE\_\_**.  
  
 En esta instrucción, el número de línea almacenado internamente se establece en 151 y el nombre de archivo se cambia a `copy.c`.  
  
```  
#line 151 "copy.c"  
```  
  
 En este ejemplo, la macro `ASSERT` utiliza las macros predefinidas **\_\_LINE\_\_** y **\_\_FILE\_\_** para imprimir un mensaje de error relativo al archivo de código fuente si una "aserción" especificada no es true.  
  
```  
#define ASSERT(cond)  
  
if( !(cond) )\  
{printf( "assertion error line %d, file(%s)\n", \  
__LINE__, __FILE__ );}  
```  
  
## Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)