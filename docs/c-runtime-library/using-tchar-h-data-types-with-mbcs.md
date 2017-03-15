---
title: "Usar tipos de datos de TCHAR.H con _MBCS | Microsoft Docs"
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
  - "_mbcs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_MBCS (tipo de datos)"
  - "MBCS (tipo de datos)"
  - "tipos de datos de TCHAR.H"
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Usar tipos de datos de TCHAR.H con _MBCS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Mientras que la tabla de asignaciones rutinarias de genérico\- texto indica \(vea [Asignaciones de Genérico\- texto](../c-runtime-library/generic-text-mappings.md)\), cuando se define `_MBCS` constante manifiesto, se asigna una rutina de genérico\- texto a uno de los siguientes tipos de rutinas:  
  
-   Una rutina de SBCS que controla cadenas, caracteres y bytes multibyte de forma apropiada.  En este caso, se espera que los argumentos de cadena son de `char*`escrito.  Por ejemplo, mapas de `_tprintf` a `printf`; los argumentos de cadena para `printf` son de `char*`escrito.  Si se utiliza el tipo de datos de genérico\- texto de `_TCHAR` para tipos de cadena, los tipos de parámetro formal y real para `printf` coinciden porque los mapas de `_TCHAR*` a `char*`.  
  
-   Una rutina específica de MBCS.  En este caso, se espera que los argumentos de cadena son de `unsigned char*`escrito.  Por ejemplo, mapas de `_tcsrev` a `_mbsrev`, que espera y devuelve una cadena de `unsigned char*`escrito.  Una vez más si se utiliza el tipo de datos de genérico\- texto de `_TCHAR` para los tipos de cadena, hay un conflicto de tipos porque los mapas de `_TCHAR` para escribir `char`.  
  
 A continuación se incluyen tres soluciones para evitar este conflicto de tipos, y las advertencias del compilador de C o los errores del compilador de C\+\+ que se obtendrán como resultado:  
  
-   Utilice el comportamiento predeterminado.  TCHAR.H proporciona el genérico\- texto prototipos de rutinas para las rutinas de las bibliotecas en tiempo de ejecución, como en el ejemplo siguiente.  
  
    ```  
    char *_tcsrev(char *);  
    ```  
  
     En el caso predeterminado, el prototipo para los mapas de `_tcsrev` a `_mbsrev` a través de un código thunk de LIBC.LIB.  Esto cambia los tipos de los parámetros de entrada de `_mbsrev` y el valor devuelto de salida de `_TCHAR *` \(como `char *`\) a `unsigned char *`.  Este método garantiza la coincidencia de tipos cuando se utiliza `_TCHAR`, pero es relativamente lento debido a la sobrecarga de la llamada de función.  
  
-   Utilice procesos en línea de función incorporando al código la siguiente instrucción de preprocesador.  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     Este método hace que el código thunk de una función inline, que en TCHAR.H, asigne la rutina de genérico\- texto directamente a la rutina de MBCS adecuada.  El siguiente fragmento de código de TCHAR.H proporciona un ejemplo de cómo se hace.  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     Si se puede realizar un proceso en línea, ésta es la mejor solución, ya que garantiza la coincidencia de tipos y no tiene un costo de tiempo adicional.  
  
-   Utilice la “asignación directa” escriba la siguiente instrucción de preprocesador en el código.  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     Este planteamiento proporciona una alternativa rápida si no se desea utilizar el comportamiento predeterminado o no se pueden realizar procesos en línea.  Hace que la rutina de genérico\- texto asignarlos por una macro directamente a la versión MBCS de la rutina, como en el siguiente ejemplo de TCHAR.H.  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
 Cuando utiliza este enfoque, debe tener cuidado para asegurarse de que utiliza los tipos de datos adecuados para los argumentos de cadena y valores devueltos de la cadena.  Puede utilizar una conversión de tipos para garantizar la coincidencia o puede utilizar el tipo de datos de genérico\- texto de `_TXCHAR` .  mapas de`_TXCHAR` para escribir `char` en código SBCS pero se asigna para escribir `unsigned char` en código MBCS.  Para obtener más información acerca de las macros de genérico\- texto, vea [Asignaciones de Genérico\- texto](../c-runtime-library/generic-text-mappings.md).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)