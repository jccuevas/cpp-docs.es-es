---
title: /Zc:throwingNew (inicia nuevo operador de asumir) | Documentos de Microsoft
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- throwingNew
- /Zc:throwingNew
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cbcb635cd37a40c2de1599d271658de308e8cff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (inicia nuevo operador de asumir)  
Cuando el `/Zc:throwingNew` se especifica la opción, el compilador optimiza las llamadas a `operator new` para omitir las comprobaciones de un puntero null devuelto. Esta opción indica al compilador que se supone que todas las implementaciones de vinculen `operator new` y asignadores personalizados se ajustan al estándar de C++ y produce una excepción durante el error de asignación. De forma predeterminada en Visual Studio, el compilador genera forma pesimista comprobaciones null (`/Zc:throwingNew-`) para estas llamadas, porque los usuarios pueden vincular mediante una implementación no produce excepciones de `operator new` o escribir rutinas de asignador personalizado que devuelven punteros null.  
  
## <a name="syntax"></a>Sintaxis  
  
`/Zc:throwingNew`[`-`]  
  
## <a name="remarks"></a>Comentarios  
  
Desde ISO C ++ 98, ha especificado el estándar que el valor predeterminado [new (operador)](../../standard-library/new-operators.md#op_new) produce `std::bad_alloc` cuando se produce un error en la asignación de memoria. Versiones de Visual C++ en Visual Studio 6.0 devuelven un puntero nulo en un error de asignación. A partir de Visual Studio 2002, `operator new` se ajusta al estándar y se produce en caso de error. Para admitir el código que utiliza el estilo de asignación anterior, Visual Studio proporciona una implementación linkable de `operator new` en *nothrownew.obj* que devuelve un puntero null en caso de error. De forma predeterminada, el compilador también genera estable comprobaciones null para impedir que estos asignadores de estilo antiguo causa un bloqueo inmediato en caso de error. El `/Zc:throwingNew` opción indica al compilador que omita estas comprobaciones de null, en la suposición de que todos los vinculados memoria asignadores conforme al estándar. Esto no se aplica a explícita no producen excepciones `operator new` sobrecargas, que se declaran mediante el uso de un parámetro adicional del tipo `std::nothrow_t` y tener explícito `noexcept` especificación.  
  
Conceptualmente, para crear un objeto en el almacén libre, el compilador genera código para asignar la memoria y, a continuación, invocar su constructor para inicializar la memoria. Dado que el compilador de Visual C++ normalmente no se puede saber si este código se vinculará a un asignador no conformes, no producen excepciones, de forma predeterminada también genera una comprobación de valores null antes de llamar al constructor. Esto evita que un puntero nulo desreferenciación en la llamada al constructor, si se produce un error en una asignación no producen excepciones. En la mayoría de los casos, estas comprobaciones son innecesarias, porque el valor predeterminado `operator new` asignadores throw en lugar de devolver punteros null. Las comprobaciones también tienen efectos secundarios indeseable. Inundación el tamaño del código, desbordan la predicción de bifurcación y no inhibe otras optimizaciones del compilador útil como devirtualization o const propagación objeto inicializado. Las comprobaciones existen únicamente al código de soporte técnico que se vincula a *nothrownew.obj* o tiene personalizado no conformes `operator new` implementaciones. Si no utiliza no conformes `operator new`, le recomendamos que use `/Zc:throwingNew` para optimizar el código.  
  
Si se compila con la generación de código en tiempo de vínculo (LTCG), no es necesario especificar `/Zc:throwingNew`. Cuando el código se compila utilizando LTCG, el compilador puede detectar si el valor predeterminado, que cumple las especificaciones `operator new` se utiliza la implementación. Si es así, el compilador omite automáticamente las comprobaciones de null. El vinculador busca la `/ThrowingNew` marca para indicar si la implementación de `operator new` se ajusta. Puede especificar esta marca al vinculador mediante la inclusión de esta directiva en el origen para la implementación del nuevo operador personalizado:  
  
```cpp  
#pragma comment(linker, "/ThrowingNew")  
```  
  
Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).  
  
## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
2.  Desde el **configuraciones** menú desplegable, elija **todas las configuraciones de**.  
3.  Seleccione el **propiedades de configuración**, **C/C++**, **línea de comandos** página de propiedades.  
4.  Modificar el **opciones adicionales** propiedad para incluir `/Zc:throwingNew` o `/Zc:throwingNew-` y, a continuación, elija **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
[/Zc (ajuste)](../../build/reference/zc-conformance.md)  
[noexcept (C++)](../../cpp/noexcept-cpp.md)  
[Especificaciones de excepciones (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)  
[Finalizar (excepción)](../../standard-library/exception-functions.md#terminate)  
