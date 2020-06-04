---
title: Directivas de preprocesador
ms.date: 08/29/2019
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
ms.openlocfilehash: 86432ebf210523dd958f3258075d9e9c6d3bb4e6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222269"
---
# <a name="preprocessor-directives"></a>Directivas de preprocesador

Las directivas de preprocesador, `#define` como y `#ifdef`, se usan normalmente para que los programas de origen sean fáciles de cambiar y compilar en diferentes entornos de ejecución. Las directivas del archivo de código fuente indican al preprocesador que realice acciones específicas. Por ejemplo, el preprocesador puede reemplazar tokens en el texto, insertar el contenido de otros archivos en el archivo de código fuente o suprimir la compilación de parte del archivo quitando secciones de texto. Las líneas de preprocesador se reconocen y se ejecutan antes de la expansión de macro. Por lo tanto, si una macro se expande en algo que se parece a un comando de preprocesador, el preprocesador no la reconoce.

Las instrucciones de preprocesador utilizan el mismo juego de caracteres que las instrucciones de archivo de código fuente, con la excepción de que no se admiten las secuencias de escape. El juego de caracteres utilizado en las instrucciones de preprocesador es el mismo que el juego de caracteres de la ejecución. El preprocesador también reconoce valores de caracteres negativos.

El preprocesador reconoce las siguientes directivas:

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

El signo de número`#`() debe ser el primer carácter que no sea un espacio en blanco en la línea que contiene la Directiva. Los caracteres de espacio en blanco pueden aparecer entre el signo de número y la primera letra de la Directiva. Algunas directivas incluyen argumentos o valores. Cualquier texto que siga a una directiva (excepto un argumento o un valor que forme parte de la Directiva) debe ir precedido de un delimitador de comentario de`//`una sola línea () o encerrado entre`/* */`delimitadores de comentario (). Las líneas que contienen directivas de preprocesador pueden continuar inmediatamente antes del marcador de fin de línea con una barra diagonal inversa (`\`).

Las directivas de preprocesador pueden aparecer en cualquier parte de un archivo de código fuente, pero solo se aplican al resto del archivo de código fuente, una vez que aparecen.

## <a name="see-also"></a>Vea también

[Operadores de preprocesador](../preprocessor/preprocessor-operators.md)\
[Macros predefinidas](../preprocessor/predefined-macros.md)\
[Referencia del preprocesador de c/c++](../preprocessor/c-cpp-preprocessor-reference.md)
