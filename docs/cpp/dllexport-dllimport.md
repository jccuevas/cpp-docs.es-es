---
title: dllexport, dllimport | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- dllimport_cpp
- dllexport_cpp
dev_langs:
- C++
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fb3495f67f674f7d65e18b985295fabf9931869
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407889"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport
**Específicos de Microsoft**  
  
 El **dllexport** y **dllimport** los atributos de clase de almacenamiento son extensiones específicas de Microsoft para los lenguajes C y C++. Se pueden utilizar para exportar e importar funciones, datos y objetos a o de una DLL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
   __declspec( dllimport ) declarator  
   __declspec( dllexport ) declarator  
```  
  
## <a name="remarks"></a>Comentarios  
 Estos atributos definen explícitamente la interfaz de la DLL para el cliente, que puede ser el archivo ejecutable u otra DLL. Declarar funciones como **dllexport** elimina la necesidad de un archivo de definición de módulo (.def), por lo menos con respecto a la especificación de funciones exportadas. El **dllexport** atributo reemplaza el **__export** palabra clave.  
  
 Si una clase está marcada con declspec(dllexport), cualquier especialización de las plantillas de clase en la jerarquía de clases se marca implícitamente como declspec(dllexport). Esto significa que se crean explícitamente instancias de las plantillas de clase y que los miembros de la clase se deben definir.  
  
 **dllexport** de una función expone la función con el nombre representativo. Para las funciones de C++, esto incluye la eliminación de nombres. Para las funciones de C o las funciones declaradas como `extern "C"`, esto incluye la decoración específica de la plataforma que se basa en la convención de llamada. Para obtener información sobre la decoración de nombres en el código de C o C++, vea [nombres representativos](../build/reference/decorated-names.md). No se aplica ninguna decoración de nombres a las funciones exportadas de C ni a las funciones `extern "C"` de C++ que usan la `__cdecl` convención de llamada.  
  
 Para exportar un nombre no representativo, puede vincular mediante un archivo de definición de módulo (.def) que define el nombre no representativo de una sección EXPORTS. Para obtener más información, consulte [exportaciones](../build/reference/exports.md). Otra forma de exportar un nombre no representativo es usar un `#pragma comment(linker, "/export:alias=decorated_name")` la directiva en el código fuente.  
  
 Al declarar **dllexport** o **dllimport**, debe usar [sintaxis de atributo extendida](../cpp/declspec.md) y **__declspec** palabra clave.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// Example of the dllimport and dllexport class attributes  
__declspec( dllimport ) int i;  
__declspec( dllexport ) void func();  
```  
  
 Opcionalmente, para que el código sea más legible, puede utilizar definiciones de macro:  
  
```cpp  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllImport int j;  
DllExport int n;  
```  
  
 Para obtener más información, consulte:  
  
-   [Definiciones y declaraciones](../cpp/definitions-and-declarations-cpp.md)  
  
-   [Definir funciones insertadas de C++ con dllexport y dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
-   [Reglas generales y limitaciones](../cpp/general-rules-and-limitations.md)  
  
-   [Usar dllimport y dllexport en las clases de C++](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)