---
title: Espacios de nombres y la visibilidad de tipos (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: cbc01a3a-3b69-4ded-9c42-ecbf0fd0a00e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4bdccc14db423d7a47545c51b31ce472f0c4308
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219526"
---
# <a name="namespaces-and-type-visibility-ccx-"></a>Visibilidad de espacios de nombres y tipos (C++/CX)
Un espacio de nombres es una construcción de C++ estándar para agrupar tipos que tienen funcionalidad relacionada y para evitar conflictos de nombre en bibliotecas. El sistema de tipos en tiempo de ejecución de Windows requiere que todos los tipos públicos de Windows Runtime, las de su propio código, incluidas se deben declarar en un espacio de nombres en el ámbito del espacio de nombres. Los tipos públicos que se declaran en el ámbito global o que se anidan dentro de otra clase producen un error en tiempo de compilación.  
  
 Un archivo .winmd debe tener el mismo nombre que el espacio de nombres de la raíz. Por ejemplo, se pueden crear instancias de una clase denominada A.B.C.MyClass solo si está definida en un archivo de metadatos denominado A.winmd, A.B.winmd o A.B.C.winmd. El nombre del ejecutable no tiene que coincidir con el nombre del archivo .winmd.  
  
## <a name="type-visibility"></a>Visibilidad de tipos  
 En un espacio de nombres, tipos de Windows Runtime, a diferencia de los tipos de C++ estándar, tener accesibilidad pública o privada. De forma predeterminada, la accesibilidad es privada. Solo un tipo público está visible para los metadatos y, por consiguiente, lo pueden utilizar aplicaciones y componentes que puedan estar escritos en lenguajes diferentes de C++. En general, las reglas para tipos visibles son más restrictivas que las reglas para tipos no visibles porque los tipos visibles no pueden exponer conceptos específicos de C++ que no se admiten en lenguajes de .NET o JavaScript.  
  
> [!NOTE]
>  Los metadatos solo se usan en tiempo de ejecución por lenguajes .NET y JavaScript. Cuando una aplicación o un componente de C++ está hablando con otra aplicación u otro componente de C++ (esto incluye a los componentes de Windows, que se escriben todos en C++), no se requiere el uso de metadatos en tiempo de ejecución.  
  
## <a name="member-accessibility-and-visibility"></a>Accesibilidad y visibilidad de miembros  
 En una clase ref, interfaz o delegado privados no se emiten miembros para metadatos, incluso si tienen accesibilidad pública. En las clases ref públicas, puedes controlar la visibilidad de los miembros en los metadatos independientemente de su accesibilidad en tu código fuente. Al igual que en C++ estándar, debes aplicar el principio de menor privilegio; no conviene que tus miembros estén visibles en los metadatos a menos que tengan que estarlo necesariamente.  
  
 Utiliza los modificadores de acceso siguientes para controlar tanto la visibilidad de los metadatos como la accesibilidad del código fuente.  
  
||||  
|-|-|-|  
|Modificador|Significado|¿Emitido para metadatos?|  
|private|La accesibilidad predeterminada. El mismo significado que en C++ estándar.|No|  
|protected|El mismo significado que en C++ estándar, tanto dentro de la aplicación o componente como en los metadatos.|Sí|  
|public|El mismo significado que en C++ estándar.|Sí|  
|`public protected` - o - `protected public`|Accesibilidad protegida en metadatos, pública dentro de la aplicación o componente.|Sí|  
|`protected private` o `private protected`|No visible en los metadatos; accesibilidad protegida dentro de la aplicación o componente.||  
|`internal` o `private public`|El miembro es público dentro de la aplicación o componente, pero no está visible en los metadatos.|No|  
  
## <a name="windows-runtime-namespaces"></a>Espacios de nombres en tiempo de ejecución de Windows  
 La API de Windows consta de tipos que se declaran en el Windows::\* espacios de nombres. Estos espacios de nombres se reservan para Windows y no se les puede agregar tipos. En el **Explorador de objetos**, puedes ver estos espacios de nombres en el archivo windows.winmd. Para obtener documentación sobre estos espacios de nombres, vea [Windows API](https://msdn.microsoft.com/library/windows/apps/br211377).  
  
## <a name="ccx-namespaces"></a>C++/CX (espacio de nombres)  
 C++ / c++ / CX define determinados tipos de espacios de nombres como parte de la proyección del sistema de tipos en tiempo de ejecución de Windows.  
  
|||  
|-|-|  
|**Espacio de nombres**|**Descripción**|  
|default|Contiene los tipos numéricos y char16 integrados. Estos tipos están en el ámbito de cada espacio de nombres y nunca se requiere una instrucción `using` .|  
|Plataforma|Contiene tipos principalmente públicos que se corresponden con los tipos en tiempo de ejecución de Windows como `Array<T>`, `String`, `Guid`, y `Boolean`. También incluye tipos auxiliares especializados como `Platform::Agile<T>` y `Platform::Box<T>`.|  
|Platform::Collections|Contiene las clases de colección concretos que implementan las interfaces de colección en tiempo de ejecución de Windows `IVector`, `IMap`, y así sucesivamente. Estos tipos se definen en un archivo de encabezado collection.h y no en platform.winmd.|  
|Platform::Details|Contiene tipos que el compilador utiliza y que no están previstos para consumo público.|  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos (C++/CX)](../cppcx/type-system-c-cx.md)