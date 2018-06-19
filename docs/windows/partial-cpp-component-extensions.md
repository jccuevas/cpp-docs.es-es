---
title: Partial (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- partial_CPP
dev_langs:
- C++
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 71c0fc9739e7ef8e1e68c5678ce56fcec4a250c1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880184"
---
# <a name="partial--c-component-extensions"></a>partial (Extensiones de componentes de C++)
El `partial` palabra clave permite que distintas partes de la misma clase ref a crearse independientemente y en archivos diferentes.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 (Esta característica de lenguaje se aplica solo a Windows Runtime).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 Para una clase ref que tiene dos definiciones parciales, la `partial` palabra clave se aplica a la primera aparición de la definición, y esto se suele realizar mediante el código generado automáticamente, por lo que un codificador humano no usa la palabra clave muy a menudo. Para todas las definiciones parciales posteriores de la clase, omita el `partial` modificador desde el *clase-clave* identificador de palabra clave y la clase. Cuando el compilador encuentra una clase ref definido anteriormente y el identificador de clase pero no `partial` palabra clave, internamente combina todas las partes de la definición de clase ref en una definición.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
partial class-key identifier {  
   /* The first part of the partial class definition. 
      This is typically auto-generated */  
}  
// ...  
class-key identifier {  
   /* The subsequent part(s) of the class definition. The same 
      identifier is specified, but the "partial" keyword is omitted. */  
}  
```  
  
### <a name="parameters"></a>Parámetros  
 *clave de la clase*  
 Una palabra clave que declara una clase o struct que es compatible con el tiempo de ejecución de Windows. Cualquier `ref class`, `value class`, `ref struct`, o `value struct`.  
  
 *identifier*  
 El nombre del tipo definido.  
  
### <a name="remarks"></a>Comentarios  
 Una clase parcial es compatible con escenarios que se modifica una parte de una definición de clase en un archivo y el software que genera código automático, por ejemplo, el Diseñador XAML, modifica el código en la misma clase en otro archivo. Mediante el uso de una clase parcial, puede impedir que el generador de código automática sobrescriba tu código. En un proyecto de Visual Studio, el modificador `partial` se aplica automáticamente al archivo generado.  
  
 Contenido: Con dos excepciones, una definición de clase parcial puede contener todo lo que podría contener la definición de clase completa si el `partial` se omite la palabra clave. Sin embargo, no se puede especificar la accesibilidad de la clase (por ejemplo, `public partial class X { ... };`), o un `declspec`.  
  
 Obtener acceso a los especificadores que se utilizan en una definición de clase parcial para *identificador* no afectan a la accesibilidad predeterminada en una definición de clase parcial o completo posteriores *identificador*. Se permiten definiciones en línea de miembros de datos estáticos.  
  
 Declaración: Una definición parcial de una clase *identificador* solo introduce el nombre *identificador*, pero *identificador* no se puede usar de forma que requiere una clase definición. El nombre *identificador* no se puede usar para conocer el tamaño de *identificador*, o usar una base o miembro de *identificador* hasta después de que el compilador encuentra la definición completa de *identificador*.  
  
 Número y el orden: puede haber cero o más definiciones de clase parcial para *identificador*. Cada definición de clase parcial de *identificador* debe preceder léxicamente a la definición completa de *identificador* (si no hay una definición completa; en caso contrario, la clase no se puede usar excepto como si declaradas por adelantado) pero no deben preceder a las declaraciones adelantadas de *identificador*. Deben coincidir con todas las claves de clase.  
  
 Completa la definición de: en el momento de la definición completa de la clase *identificador*, el comportamiento es el mismo como si la definición de *identificador* hubiera declarado todas las clases base, miembros, etc. en el orden en que se encontraron y se definen en las clases parciales.  
  
 Plantillas: Una clase parcial no puede ser una plantilla.  
  
 Genéricos: Una clase parcial puede ser un tipo genérico si la definición completa podría ser genérica. Pero cada clase parcial y completa debe tener exactamente los mismos parámetros genéricos, incluidos los nombres de parámetros formales.  
  
 Para obtener más información sobre cómo usar el `partial` palabra clave, consulte [clases parciales (C++ / CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 (Esta característica de lenguaje no se aplica a Common Language Runtime.)  
  
## <a name="see-also"></a>Vea también  
 [Clases parciales (C++ / CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)