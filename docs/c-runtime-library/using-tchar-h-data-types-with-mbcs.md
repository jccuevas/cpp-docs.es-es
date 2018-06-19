---
title: Uso de tipos de datos de TCHAR.H con MBCS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 066459593be4970fde141333a6f22f0846f8bbc4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412656"
---
# <a name="using-tcharh-data-types-with-mbcs"></a>Usar tipos de datos de TCHAR.H con _MBCS

**Específicos de Microsoft**

Tal y como se indica en la tabla de asignaciones de rutina de texto genérico (vea [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md)), cuando se define la constante de manifiesto **_MBCS**, se asigna una rutina de texto genérico determinada a uno de los siguientes tipos de rutinas:

- Una rutina de SBCS que controla cadenas, caracteres y bytes multibyte de forma adecuada. En este caso, se espera que los argumentos de cadena sean del tipo **char&#42;**. Por ejemplo, **_tprintf** se asigna a **printf**; los argumentos de cadena para **printf** son de tipo **char&#42;**. Si usa el tipo de datos de texto genérico **_TCHAR** para los tipos de cadena, los tipos de parámetros formales y reales de **printf** coinciden porque **_TCHAR&#42;** se asigna a **char&#42;**.

- Una rutina específica de MBCS. En este caso, se espera que los argumentos de cadena sean del tipo __char&#42; sin signo__. Por ejemplo, **_tcsrev** se asigna a **_mbsrev**, que espera y devuelve una cadena de tipo __char&#42; sin signo__. Una vez más, si usa el tipo de datos de texto genérico **_TCHAR** para los tipos de cadena, hay un posible conflicto de tipos porque **_TCHAR** se asigna al tipo **char**.

 A continuación se presentan tres soluciones para evitar este conflicto de tipos, así como las advertencias del compilador de C o errores del compilador de C++ que se generarían:

- Usa el comportamiento predeterminado. TCHAR.H proporciona prototipos de rutinas de texto genérico para rutinas en las bibliotecas en tiempo de ejecución, como en el ejemplo siguiente.

   ```C
   char *_tcsrev(char *);
   ```

   En el caso predeterminado, el prototipo de **_tcsrev** se asigna a **_mbsrev** a través de un código thunk en LIBC.LIB. Esto cambia los parámetros de entrada y el valor devuelto de salida **_mbsrev** de **_TCHAR &#42;** (como **char &#42;**) a **char &#42; sin signo**. Este método garantiza la coincidencia de tipos cuando se usa **_TCHAR**, pero es relativamente lento debido a la sobrecarga de la llamada a la función.

- Use la inserción de funciones mediante la incorporación de la siguiente instrucción del preprocesador en el código.

   ```C
   #define _USE_INLINING
   ```

   Este método genera un código thunk de la función insertada, proporcionado en TCHAR.H, para asignar la rutina de texto genérico directamente a la rutina de MBCS adecuada. El siguiente fragmento de código de TCHAR.H proporciona un ejemplo de cómo hacerlo.

   ```C
   __inline char *_tcsrev(char *_s1)
   {return (char *)_mbsrev((unsigned char *)_s1);}
   ```

   Si puede usar la inserción, es la mejor solución, ya que garantiza la coincidencia de tipos y no incurrir en ningún costo por tiempo adicional.

- Use la "asignación directa" mediante la incorporación de la siguiente instrucción del preprocesador en el código.

   ```C
   #define _MB_MAP_DIRECT
   ```

   Este enfoque proporciona una alternativa rápida si no desea usar el comportamiento predeterminado o si no se puede usar la inserción. Hace que la rutina de texto genérico se asigne directamente a la versión de MBCS de la rutina, como en el siguiente ejemplo de TCHAR.H.

   ```C
   #define _tcschr _mbschr
   ```

Al adoptar este enfoque, debe asegurarse de que se utilizan tipos de datos apropiados para argumentos de cadena y valores devueltos de cadena. Puede usar la conversión de tipos para garantizar la coincidencia correcta de tipos o puede usar el tipo de datos de texto genérico **_TXCHAR**. **_TXCHAR** se asigna al tipo **char** en código SBCS pero se asigna al tipo **char sin signo** en código MBCS. Para más información sobre las macros de texto genérico, vea [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Internacionalización](../c-runtime-library/internationalization.md)<br/>
[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
