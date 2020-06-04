---
title: Utilizar tipos de datos de TCHAR.H con código _MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: 78e5d89e1e87d081e762fab1298eb990b914324c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446593"
---
# <a name="using-tcharh-data-types-with-_mbcs-code"></a>Utilizar tipos de datos de TCHAR.H con código _MBCS

Cuando se define la constante de manifiesto `_MBCS`, se asigna una rutina de texto genérico determinada a uno de los siguientes tipos de rutinas:

- Una rutina de SBCS que controla cadenas, caracteres y bytes multibyte de forma adecuada. En este caso, se espera que los argumentos de cadena sean del tipo `char*`. Por ejemplo, `_tprintf` se asigna a `printf`; los argumentos de cadena para `printf` son de tipo `char*`. Si usa el tipo de datos de texto genérico `_TCHAR` para la cadena de tipos, los tipos de parámetros formales y reales para `printf` coinciden porque `_TCHAR*` se asigna a `char*`.

- Una rutina específica de MBCS. En este caso, se espera que los argumentos de cadena sean del tipo `unsigned char*`. Por ejemplo, `_tcsrev` se asigna a `_mbsrev`, que espera y devuelve una cadena de tipo `unsigned char*`. Si usa el tipo de datos de texto genérico `_TCHAR` para los tipos de cadena, hay un posible conflicto de tipos porque `_TCHAR` se asigna al tipo `char`.

A continuación se presentan tres soluciones para evitar este conflicto de tipos, así como las advertencias del compilador de C o errores del compilador de C++ que se generarían:

- Usa el comportamiento predeterminado. TCHAR. h proporciona prototipos de rutina de texto genérico para las rutinas de las bibliotecas en tiempo de ejecución, como en el ejemplo siguiente.

    ```cpp
    char * _tcsrev(char *);
    ```

   En el caso predeterminado, el prototipo de `_tcsrev` se asigna a `_mbsrev` a través de un código thunk en libc. lib. Esto cambia los tipos de `_mbsrev` parámetros entrantes y el valor devuelto saliente de `_TCHAR*` (es decir, `char *`) a `unsigned char *`. Este método garantiza la coincidencia de tipos cuando se usa `_TCHAR`, pero es relativamente lento debido a la sobrecarga de la llamada de función.

- Use la inserción de funciones mediante la incorporación de la siguiente instrucción del preprocesador en el código.

    ```cpp
    #define _USE_INLINING
    ```

   Este método produce un código thunk de función insertada, proporcionado en TCHAR. h, para asignar la rutina de texto genérico directamente a la rutina de MBCS adecuada. El siguiente fragmento de código de TCHAR. h proporciona un ejemplo de cómo hacerlo.

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   Si puede usar la inserción, es la mejor solución, ya que garantiza la coincidencia de tipos y no incurrir en ningún costo por tiempo adicional.

- Use la asignación directa mediante la incorporación de la siguiente instrucción de preprocesador en el código.

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   Este enfoque proporciona una alternativa rápida si no desea usar el comportamiento predeterminado o si no se puede usar la inserción. Hace que la rutina de texto genérico se asigne a una macro directamente a la versión MBCS de la rutina, como en el ejemplo siguiente de TCHAR. h.

    ```cpp
    #define _tcschr _mbschr
    ```

   Al adoptar este enfoque, debe asegurarse de usar los tipos de datos adecuados para los argumentos de cadena y los valores devueltos de cadena. Puede usar la conversión de tipos para garantizar la coincidencia correcta de tipos o puede usar el tipo de datos de texto genérico `_TXCHAR`. `_TXCHAR` se asigna al tipo **Char** en el código SBCS pero se asigna al tipo **Char sin signo** en el código MBCS. Para obtener más información sobre las macros de texto genérico, vea [asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md) en la referencia de la *biblioteca en tiempo de ejecución*.

## <a name="see-also"></a>Consulte también

[Asignaciones de texto genérico en tchar.h](../text/generic-text-mappings-in-tchar-h.md)
