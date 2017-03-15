---
title: "Utilizar tipos de datos de TCHAR.H con c&#243;digo _MBCS | Microsoft Docs"
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
  - ""tchar.h""
  - "TCHAR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos de datos de texto genérico [C++]"
  - "asignaciones de texto genérico [C++]"
  - "asignar texto genérico"
  - "asignaciones [C++], TCHAR.H"
  - "MBCS [C++], asignaciones de texto genérico"
  - "tipos de datos de TCHAR.H, asignar"
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Utilizar tipos de datos de TCHAR.H con c&#243;digo _MBCS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando la constante de manifiesto **\_MBCS** está definida, se asigna una rutina de texto genérico determinada a uno de los siguientes tipos de rutinas:  
  
-   Una rutina de SBCS que controla cadenas, caracteres y bytes multibyte de forma apropiada.  En este caso, se espera que los argumentos de la cadena sean del tipo **char\***.  Por ejemplo, `_tprintf` se asigna a `printf`; los argumentos de la cadena a `printf` son del tipo **char\***.  Si se utiliza el tipo de datos de texto genérico **\_TCHAR** para los tipos de cadena, los tipos de parámetro formal y real para `printf` coinciden, porque \_**TCHAR**\* se asigna a **char\***.  
  
-   Una rutina específica de MBCS.  En este caso, se espera que los argumentos de la cadena sean de tipo `unsigned` **char\***.  Por ejemplo, `_tcsrev` se asigna a `_mbsrev`, que espera y devuelve una cadena de tipo `unsigned` **char\***.  Si se utiliza el tipo de datos de texto genérico **\_TCHAR** para los tipos de cadena, puede producirse un conflicto de tipos porque **\_TCHAR** se asigna al tipo `char`.  
  
 A continuación se incluyen tres soluciones para evitar este conflicto de tipos, y las advertencias del compilador de C o los errores del compilador de C\+\+ que se obtendrán como resultado:  
  
-   Utilice el comportamiento predeterminado.  Tchar.h proporciona prototipos de rutinas de texto genérico para las rutinas de las bibliotecas en tiempo de ejecución, como en el siguiente ejemplo.  
  
    ```  
    char * _tcsrev(char *);  
    ```  
  
     En el caso predeterminado, el prototipo de `_tcsrev` se asigna a `_mbsrev` a través de un código thunk de Libc.lib.  De esta forma, los tipos de los parámetros de entrada y del valor devuelto de salida de `_mbsrev` cambian de **\_TCHAR \*** \(es decir, `char` **\***\) a `unsigned` `char` **\***.  Este método garantiza la coincidencia de tipos cuando se utiliza **\_TCHAR**, pero es relativamente lento debido a la sobrecarga de la llamada a la función.  
  
-   Utilice procesos en línea de función incorporando al código la siguiente instrucción de preprocesador.  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     Este método hace que el código thunk de una función inline, que se proporciona en Tchar.h, asigne la rutina de texto genérico directamente a la rutina de MBCS adecuada.  En el siguiente fragmento de código de Tchar.h se proporciona un ejemplo sobre la forma de realizar este proceso.  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     Si se puede realizar un proceso en línea, ésta es la mejor solución, ya que garantiza la coincidencia de tipos y no tiene un costo de tiempo adicional.  
  
-   Utilice la asignación directa incorporando al código la siguiente instrucción de preprocesador.  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     Este planteamiento proporciona una alternativa rápida si no se desea utilizar el comportamiento predeterminado o no se pueden realizar procesos en línea.  Provoca la asignación directa de la rutina de texto genérico, mediante una macro, a la versión MBCS de la rutina, como en el siguiente ejemplo de Tchar.h.  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
     Si se elige este planteamiento, conviene asegurarse del uso de los tipos de datos adecuados para los argumentos de cadena y los valores devueltos de cadenas.  Se puede utilizar una conversión de tipos para garantizar la coincidencia correcta de tipos o utilizar el tipo de datos de texto genérico **\_TXCHAR**.  **\_TXCHAR** se asigna al tipo `char` en código SBCS pero se asigna al tipo `unsigned` `char` en código MBCS.  Para obtener más información acerca de las macros de texto genérico, vea [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md) en la *Referencia de la biblioteca en tiempo de ejecución*.  
  
## Vea también  
 [Asignaciones de texto genérico en TCHAR.H](../Topic/Generic-Text%20Mappings%20in%20Tchar.h.md)