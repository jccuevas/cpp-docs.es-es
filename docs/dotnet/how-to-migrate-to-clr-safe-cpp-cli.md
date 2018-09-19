---
title: 'Cómo: migrar a clr-: seguro (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- migration [C++], verifiable assemblies
- upgrading Visual C++ applications, verifiable assemblies
- verifiable assemblies [C++], migrating to
- /clr compiler option [C++], migrating to /clr:safe
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d72be19eb893a74a17a988e8c14c6bdaba766cbc
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704519"
---
# <a name="how-to-migrate-to-clrsafe-ccli"></a>Cómo: Migrar a /clr:safe (C++/CLI)

> [!IMPORTANT]
> El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017. Si tiene ensamblados safe de CLR, se recomienda que trasladar el código a C#.

Si está utilizando una versión anterior de la herramientas de compilador de Visual C++ desde antes de 2017 de Visual Studio, puede generar componentes comprobables mediante **/CLR: safe**, lo que hace que el compilador genere errores para cada uno de ellos no es comprobable construcción de código.

## <a name="remarks"></a>Comentarios

Los problemas siguientes generan errores de capacidad:

- Tipos nativos. Incluso si no se utiliza, la declaración de clases nativas, estructuras, punteros o matrices impide la compilación.

- Variables globales

- Llamadas a funciones en cualquier biblioteca no administrada, tales como llamadas de función de en tiempo de ejecución de lenguaje común

- Una función comprobable no puede contener una [static_cast (operador)](../cpp/static-cast-operator.md) para convertir. El [static_cast (operador)](../cpp/static-cast-operator.md) puede usarse para convertir entre tipos primitivos, pero para conversión de abajo, [safe_cast](../windows/safe-cast-cpp-component-extensions.md) o una conversión de estilo C (que se implementa como un [safe_cast](../windows/safe-cast-cpp-component-extensions.md)) se debe usar.

- Una función comprobable no puede contener una [reinterpret_cast (operador)](../cpp/reinterpret-cast-operator.md) (ni ningún equivalente de conversión de estilo C).

- Una función comprobable no realiza operaciones aritméticas en un [interior_ptr (C++ / CLI)](../windows/interior-ptr-cpp-cli.md). Solo puede asignar a él y desreferenciar esta variable.

- Una función comprobable sólo puede producir o detectar punteros a tipos de referencia, por lo que deben someterse conversión boxing de tipos de valor antes de iniciar.

- Una función comprobable solo puede llamar a funciones comprobables (incluir de forma que no se permiten llamadas a common language runtime, `AtEntry` / `AtExit`, de modo que los constructores globales no están permitidos).

- No se puede usar una clase comprobable <xref:System.Runtime.InteropServices.LayoutKind>.

- Si crea un archivo EXE, una función principal no puede declarar ningún parámetro, por lo que <xref:System.Environment.GetCommandLineArgs%2A> debe usarse para recuperar argumentos de línea de comandos.

- Realiza una llamada no virtual a una función virtual. Por ejemplo:

   ```cpp
   // not_verifiable.cpp
   // compile with: /clr
   ref struct A {
      virtual void Test() {}
   };

   ref struct B : A {};

   int main() {
      B^ b1 = gcnew B;
      b1->A::Test();   // Non-virtual call to virtual function
   }
   ```

Además, las siguientes palabras clave no se puede usar en código comprobable:

- [no administrado](../preprocessor/managed-unmanaged.md) y [pack](../preprocessor/pack.md) pragma (directivas)

- [naked](../cpp/naked-cpp.md) y [alinear](../cpp/align-cpp.md) [__declspec](../cpp/declspec.md) modificadores

- [__asm](../assembler/inline/asm.md)

- [__based](../cpp/based-grammar.md)

- [__try](../cpp/try-except-statement.md) y `__except`

## <a name="see-also"></a>Vea también

- [Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
