---
title: '#Using (directivaC++) (/CLI)'
ms.date: 08/29/2019
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: 5dae5c277055157aef5451c19ee020fbbd2aaccb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220202"
---
# <a name="using-directive-ccli"></a>#using (directivaC++) (/CLI)

Importa los metadatos en un programa compilado con [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Sintaxis

> **#using** *archivo* de [**as_friend**]

### <a name="parameters"></a>Parámetros

*filesystem*\
Archivo .dll, .exe, .netmodule u .obj de MSIL. Por ejemplo,

`#using <MyComponent.dll>`

**as_friend**\
Especifica que se puede tener acceso a todos los tipos del *archivo* . Para obtener más información, vea [ensambladosC++de confianza ()](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Comentarios

el *archivo* puede ser un archivo de lenguaje intermedio de Microsoft (MSIL) que se importa para sus construcciones administradas y datos administrados. Si un archivo. dll contiene un manifiesto de ensamblado, se importarán todos los archivos. dll a los que se hace referencia en el manifiesto y el ensamblado que se va a compilar mostrará el *archivo* en los metadatos como una referencia de ensamblado.

Si el *archivo* no contiene un ensamblado (si el *archivo* es un módulo) y si no piensa usar información de tipos del módulo en la aplicación (ensamblado) actual, tiene la opción de indicar simplemente que el módulo forma parte del ensamblado. Use [/assemblymodule](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Los tipos del módulo estarán disponibles entonces para cualquier aplicación que hiciera referencia al ensamblado.

Una alternativa al uso de **#using** es la opción del compilador [/Fu](../build/reference/fu-name-forced-hash-using-file.md) .

los ensamblados. exe pasados a **#using** se deben compilar mediante uno de los compiladores de .net Visual Studio C#(Visual Basic o visual, por ejemplo).  Si se intenta importar metadatos de un ensamblado .exe compilado con `/clr`, se producirá una excepción de carga del archivo.

> [!NOTE]
> Un componente al que se hace referencia con **#using** se puede ejecutar con una versión diferente del archivo importado en tiempo de compilación, lo que hace que una aplicación cliente proporcione resultados inesperados.

Para que el compilador reconozca un tipo de un ensamblado (no de un módulo), debe ser obligado a resolver el tipo. Puede forzarlo, por ejemplo, definiendo una instancia del tipo. Hay otras maneras de resolver nombres de tipos en un ensamblado para el compilador. Por ejemplo, si se hereda de un tipo de un ensamblado, el compilador conoce el nombre del tipo.

Al importar metadatos generados a partir del código fuente que usaba [_ _ declspec (subproceso)](../cpp/thread.md), la semántica de subprocesos no se conserva en los metadatos. Por ejemplo, una variable declarada con **_ _ declspec (Thread)** , compilada en un programa compilado para el .NET Framework Common Language Runtime y, a continuación, importado a través de **#using**, no tendrá la semántica de **_ _ declspec (Thread)** en la variable.

Todos los tipos importados (tanto administrados como nativos) en un archivo al que hace referencia **#using** están disponibles, pero el compilador trata los tipos nativos como declaraciones, no definiciones.

Se hace referencia automáticamente a mscorlib.dll cuando se compila con `/clr`.

La variable de entorno LIBPATH especifica los directorios en los que buscar cuando el compilador resuelve los nombres de archivo pasados a **#using**.

El compilador busca referencias a lo largo de la ruta de acceso siguiente:

- Ruta de acceso especificada en la instrucción **#using** .

- El directorio actual.

- El directorio del sistema de .NET Framework.

- Directorios agregados con la opción [/AI](../build/reference/ai-specify-metadata-directories.md) del compilador.

- Directorios de la variable de entorno LIBPATH.

## <a name="example"></a>Ejemplo

Si crea un ensamblado (C) y hace referencia a un ensamblado (B) que hace referencia a otro ensamblado (A), no tendrá que hacer referencia explícitamente al ensamblado A a menos que utilice explícitamente uno de los tipos de A en C.

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

## <a name="example"></a>Ejemplo

```cpp
// using_assembly_B.cpp
// compile with: /clr /LD
#using "using_assembly_A.dll"
public ref class B {
public:
   void Test(A a) {}
   void Test() {}
};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, no hay ningún error del compilador para no hacer referencia a *using_assembly_A. dll*, porque el programa no usa ninguno de los tipos definidos en *using_assembly_A. cpp*.

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)
