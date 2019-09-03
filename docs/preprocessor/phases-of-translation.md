---
title: Fases de traducción
ms.date: 08/29/2019
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
ms.openlocfilehash: d072c9aec48d815ba85f8a12576baa6447703f8c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218306"
---
# <a name="phases-of-translation"></a>Fases de traducción

Los programas de C y C++ constan de uno o más archivos de código fuente, cada uno de los cuales contiene parte del texto de programa. Un archivo de código fuente, junto con sus *archivos de inclusión*, los archivos que `#include` se incluyen con la Directiva de preprocesador, pero sin incluir las secciones de código que se han `#if`quitado mediante directivas de compilación condicional como, se denomina  *unidad de traducción*.

Los archivos de origen se pueden traducir en momentos diferentes. De hecho, es habitual traducir solo los archivos no actualizados. Las unidades de traducción traducidas se pueden procesar en archivos de objetos o bibliotecas de código de objetos independientes. Estas unidades de traducción independientes traducidas se vinculan para formar un programa ejecutable o una biblioteca de vínculos dinámicos (DLL). Para obtener más información acerca de los archivos que se pueden usar como entrada para el vinculador, vea [vincular archivos de entrada](../build/reference/link-input-files.md).

Las unidades de traducción pueden comunicarse mediante:

- Llamadas a funciones que tienen vinculación externa.

- Llamadas a funciones miembro de clase que tienen vinculación externa.

- Modificación directa de objetos que tienen vinculación externa.

- Modificación directa de archivos.

- Comunicación entre procesos (solo para aplicaciones basadas en Microsoft Windows).

La lista siguiente describe las fases en las que el compilador traduce los archivos:

*Asignación de caracteres*\
Los caracteres del archivo de código fuente se asignan a la representación de código fuente interna. En esta fase, las secuencias de trígrafos se convierten en una representación interna de caracteres únicos.

*Inserción de líneas*\
Todas las líneas que terminan en una **\\** barra diagonal inversa () seguidas inmediatamente por un carácter de nueva línea se unen con la siguiente línea del archivo de código fuente, formando las líneas lógicas de las líneas físicas. A menos que esté vacío, un archivo de código fuente debe terminar en un carácter de nueva línea que no esté precedido por una barra diagonal inversa.

*Tokenización*\
El archivo de código fuente se divide en tokens de preprocesamiento y caracteres de espacio en blanco. Cada uno de los comentarios del archivo de código fuente se reemplaza por un carácter de espacio. Los caracteres de nueva línea se conservan.

*Preprocesamiento*\
Se ejecutan las directivas de preprocesamiento y se expanden las macros al archivo de código fuente. La instrucción `#include` invoca la traslación que comienza con los tres pasos anteriores de traslación en cualquier texto incluido.

*Asignación de juegos de caracteres*\
Todos los miembros y secuencias de escape de juego de caracteres de origen se convierten en sus equivalentes en el juego de caracteres de ejecución. Para Microsoft C y C++, tanto el juego de caracteres de ejecución de origen como el de ejecución son ASCII.

*Concatenación de cadenas*\
Se concatenan todos los literales adyacentes de cadena y cadena de caracteres anchos. Por ejemplo, `"String " "concatenation"` se convierte en `"String concatenation"`.

*Automática*\
Todos los tokens se analizan sintáctica y semánticamente; estos tokens se convierten en código de objeto.

*Transmisión*\
Se resuelven todas las referencias externas para crear un programa ejecutable o una biblioteca de vínculos dinámicos.

El compilador produce advertencias o errores durante las fases de traslación en las que encuentra errores de sintaxis.

El vinculador resuelve todas las referencias externas y crea un programa ejecutable o DLL combinando una o más unidades de traslación procesadas por separado junto con bibliotecas estándar.

## <a name="see-also"></a>Vea también

[Preprocesador](../preprocessor/preprocessor.md)
