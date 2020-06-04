---
title: Compatibilidad con COM del compilador
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 6ab697e5a090158b034a385e60978cff4a73f488
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857585"
---
# <a name="compiler-com-support"></a>Compatibilidad con COM del compilador

**Específicos de Microsoft**

El compilador de Microsoft C++ puede leer directamente bibliotecas de tipos de modelo de objetos componentes (com C++ ) y traducir el contenido en código fuente que se puede incluir en la compilación. Las extensiones de lenguaje están disponibles para facilitar la programación COM en el lado cliente de las aplicaciones de escritorio.

Mediante el uso de la [Directiva de preprocesador de #import](../preprocessor/hash-import-directive-cpp.md), el compilador puede leer una biblioteca de C++ tipos y convertirla en un archivo de encabezado que describe las interfaces com como clases. Existe un conjunto de atributos `#import` disponible para el control por parte del usuario del contenido de los archivos de encabezado de biblioteca de tipos resultantes.

Puede usar el UUID [__declspec](../cpp/declspec.md) atributo extendido [uuid](../cpp/uuid-cpp.md) para asignar un identificador único global (GUID) a un objeto com. La palabra clave [__uuidof](../cpp/uuidof-operator.md) se puede utilizar para extraer el GUID asociado a un objeto com. Otro atributo **__declspec** , [propiedad](../cpp/property-cpp.md), se puede utilizar para especificar los métodos `get` y `set` para un miembro de datos de un objeto com.

Se proporciona un conjunto de funciones y clases globales de compatibilidad con COM para admitir los tipos `VARIANT` y `BSTR`, implementar punteros inteligentes y encapsular el objeto de error que produce `_com_raise_error`:

- [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)<br/>
[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)
