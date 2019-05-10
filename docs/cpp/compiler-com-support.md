---
title: Compatibilidad con COM del compilador
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: e13874bad44610821bed9c588af6bd9124162116
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222212"
---
# <a name="compiler-com-support"></a>Compatibilidad con COM del compilador

## <a name="microsoft-specific"></a>Específicos de Microsoft

Microsoft C++ directamente, el compilador pueda leer las bibliotecas de tipos de componente objeto COM (modelo) y traducir el contenido en C++ código fuente que puede incluirse en la compilación. Existen extensiones de lenguaje disponibles para facilitar la programación COM en el cliente.

Mediante el uso de la [directiva de preprocesador #import](../preprocessor/hash-import-directive-cpp.md), el compilador puede leer una biblioteca de tipos y convertir las interfaces en un archivo de encabezado de C++ que describe el COM como clases. Existe un conjunto de atributos `#import` disponible para el control por parte del usuario del contenido de los archivos de encabezado de biblioteca de tipos resultantes.

Puede usar el [__declspec](../cpp/declspec.md) atributo extendido [uuid](../cpp/uuid-cpp.md) para asignar un identificador único global (GUID) a un objeto COM. La palabra clave [__uuidof](../cpp/uuidof-operator.md) puede utilizarse para extraer el GUID asociado a un objeto COM. Otro **__declspec** atributo, [propiedad](../cpp/property-cpp.md), puede utilizarse para especificar el `get` y `set` métodos para un miembro de datos de un objeto COM.

Se proporciona un conjunto de clases y funciones globales de soporte técnico de COM para admitir la `VARIANT` y `BSTR` tipos, implementar punteros inteligentes y encapsular el objeto de error iniciado por `_com_raise_error`:

- [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)<br/>
[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)