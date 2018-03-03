---
title: "Mediante TCHAR. Tipos de datos de H con código _MBCS | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tchar.h
- TCHAR
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28255b2e47c48b89b0bd6aea044fe0c15c1f2a08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>Utilizar tipos de datos de TCHAR.H con código _MBCS
Cuando la constante de manifiesto **_MBCS** está definido, se asigna una rutina de texto genérico determinada a uno de los siguientes tipos de rutinas:  
  
-   Una rutina de SBCS que controla cadenas, caracteres y bytes multibyte de forma adecuada. En este caso, se espera que los argumentos de cadena del tipo **char\***. Por ejemplo, `_tprintf` se asigna a `printf`; los argumentos de cadena para `printf` son de tipo **char\***. Si usas el **_TCHAR** tipo de datos de texto genérico para la cadena de tipos, los tipos de parámetros formales y reales para `printf` coinciden porque **_TCHAR** \* se asigna a **char \***.  
  
-   Una rutina específica de MBCS. En este caso, se espera que los argumentos de cadena del tipo `unsigned` **char\***. Por ejemplo, `_tcsrev` se asigna a `_mbsrev`, que espera y devuelve una cadena de tipo `unsigned` **char\***. Si usas el **_TCHAR** tipo de datos de texto genérico para los tipos de cadena, hay un conflicto de tipos porque **_TCHAR** se asigna al tipo `char`.  
  
 A continuación se presentan tres soluciones para evitar este conflicto de tipos, así como las advertencias del compilador de C o errores del compilador de C++ que se generarían:  
  
-   Usa el comportamiento predeterminado. Tchar.h proporciona prototipos de rutinas de texto genérico para rutinas en las bibliotecas en tiempo de ejecución, como en el ejemplo siguiente.  
  
    ```  
    char * _tcsrev(char *);  
    ```  
  
     En el caso predeterminado, el prototipo de `_tcsrev` se asigna a `_mbsrev` a través de un código thunk de Libc.lib. Esto cambia los tipos de la `_mbsrev` parámetros entrantes y salientes devuelven el valor de **_TCHAR \***  (es decir, `char`  **\*** ) a `unsigned` `char` **\***. Este método garantiza la coincidencia de tipos cuando utilizas **_TCHAR**, pero es relativamente lento debido a la sobrecarga de la llamada de función.  
  
-   Use la inserción de funciones mediante la incorporación de la siguiente instrucción del preprocesador en el código.  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     Este método provoca un thunk de función inline, que se proporcionan en Tchar.h, para asignar la rutina de texto genérico directamente a la rutina MBCS adecuada. El siguiente fragmento de código de Tchar.h proporciona un ejemplo de cómo hacerlo.  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     Si puede usar la inserción, es la mejor solución, ya que garantiza la coincidencia de tipos y no incurrir en ningún costo por tiempo adicional.  
  
-   Utilice la asignación directa mediante la incorporación de la siguiente instrucción de preprocesador en el código.  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     Este enfoque proporciona una alternativa rápida si no desea usar el comportamiento predeterminado o si no se puede usar la inserción. Hace que la rutina de texto genérico para una macro asignarse directamente a la versión MBCS de la rutina, como en el ejemplo siguiente en Tchar.h.  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
     Al adoptar este enfoque, debe garantizar el uso de tipos de datos apropiados para los argumentos de cadena y valores devueltos de cadenas. Puede usar la conversión de tipos para garantizar la coincidencia correcta de tipos o puede usar el **_TXCHAR** tipo de datos de texto genérico. **_TXCHAR** se asigna al tipo `char` en código SBCS pero se asigna al tipo `unsigned` `char` en código MBCS. Para obtener más información acerca de las macros de texto genérico, vea [asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md) en el *referencia de la biblioteca de tiempo de ejecución*.  
  
## <a name="see-also"></a>Vea también  
 [Asignaciones de texto genérico en TCHAR.H](../text/generic-text-mappings-in-tchar-h.md)