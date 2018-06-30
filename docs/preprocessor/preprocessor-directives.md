---
title: Directivas de preprocesador | Documentos de Microsoft
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5621c1a338ea6870d15dca65c303d4ac2bf8c7a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122600"
---
# <a name="preprocessor-directives"></a>Directivas de preprocesador

Directivas de preprocesador, como `#define` y **#ifdef**, se utilizan normalmente para que los programas de origen sean fáciles de modificar y compilar en diferentes entornos de ejecución. Las directivas del archivo de código fuente indican al preprocesador que realice acciones específicas. Por ejemplo, el preprocesador puede reemplazar tokens en el texto, insertar el contenido de otros archivos en el archivo de código fuente o suprimir la compilación de parte del archivo quitando secciones de texto. Las líneas de preprocesador se reconocen y se ejecutan antes de la expansión de macro. Por consiguiente, si una macro se expande en algo que se parezca a un comando de preprocesador, el preprocesador no reconocerá ese comando.

Las instrucciones de preprocesador utilizan el mismo juego de caracteres que las instrucciones del archivo de código fuente, con la excepción de que no se admiten secuencias de escape. El juego de caracteres utilizado en las instrucciones de preprocesador es el mismo que el [juego de caracteres de ejecución](http://msdn.microsoft.com/en-us/a7901c61-524d-47c6-beb6-d9dacc2e72ed). El preprocesador también reconoce valores de caracteres negativos.

El preprocesador reconoce las siguientes directivas:

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

El signo de número (**#**) debe ser el primer carácter de espacio en blanco en la línea que contiene la directiva; pueden aparecer caracteres de espacio en blanco entre el signo de número y la primera letra de la directiva. Algunas directivas incluyen argumentos o valores. Cualquier texto que sigue a una directiva (excepto un argumento o un valor que forme parte de la directiva) debe ir precedido por un delimitador de comentario de línea única (**//**) o incluido entre delimitadores de comentario ( __/ \*\*/__).   Líneas que contienen directivas de preprocesador pueden continuar precediendo inmediatamente el marcador de fin de línea con una barra diagonal inversa (**\\**).

Las directivas de preprocesador pueden aparecer en cualquier lugar de un archivo de código fuente, pero solo se aplican al resto del archivo de código fuente.

## <a name="see-also"></a>Vea también

[Operadores de preprocesador](../preprocessor/preprocessor-operators.md)  
[Macros predefinidas](../preprocessor/predefined-macros.md)  
[Referencia del preprocesador de C/C++](../preprocessor/c-cpp-preprocessor-reference.md)  
