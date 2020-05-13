---
title: '#import (atributos) (C++)'
ms.date: 08/29/2019
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: fc2af69025d47a9ea6cea0e2c9e1423151b01606
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215298"
---
# <a name="import-attributes-c"></a>atributos #import (C++)

Proporciona vínculos a los atributos utilizados con la Directiva de `#import`.

**Específicos de Microsoft**

Los siguientes atributos están disponibles para la Directiva `#import`.

|Atributo|Descripción|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|Cambia de nombre las palabras reservadas de C++ al anexar dos caracteres de subrayado (__) al nombre de la variable para resolver posibles conflictos de nombre.|
|[auto_search](../preprocessor/auto-search.md)|Especifica que, cuando se hace referencia a una biblioteca de tipos mediante #import y ella misma hace referencia a otra biblioteca de tipos, el compilador puede realizar un #import implícito para la otra biblioteca de tipos.|
|[embedded_idl](../preprocessor/embedded-idl.md)|Especifica que la biblioteca de tipos se escriba en el archivo .tlh, conservando el código generado por el atributo.|
|[exclude](../preprocessor/exclude-hash-import.md)|Excluye elementos de los archivos de encabezado de la biblioteca de tipos que se generan.|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|Especifica un prefijo que se utilizará para designar propiedades y métodos de alto nivel.|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|Especifica los prefijos alternativos para tres métodos de propiedad.|
|[implementation_only](../preprocessor/implementation-only.md)|Suprime la generación de archivos de encabezado .tlh (el archivo de encabezado principal).|
|[include()](../preprocessor/include-parens.md)|Deshabilita la exclusión automática.|
|[inject_statement](../preprocessor/inject-statement.md)|Inserta el argumento como texto original en el encabezado de la biblioteca de tipos.|
|[named_guids](../preprocessor/named-guids.md)|Indica al compilador que defina e inicialice las variables GUID en el estilo anterior, con el formato `LIBID_MyLib`, `CLSID_MyCoClass`, `IID_MyInterface`y `DIID_MyDispInterface`.|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Deshabilita la exclusión automática.|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Cambia la manera en que el compilador genera las funciones de contenedor para los métodos de interfaz dual.|
|[no_implementation](../preprocessor/no-implementation.md)|Suprime la generación del encabezado .tli, que contiene las implementaciones de las funciones miembro de contenedor.|
|[no_namespace](../preprocessor/no-namespace.md)|Especifica que el compilador no genera el espacio de nombres.|
|[no_registry](../preprocessor/no-registry.md)|Indica al compilador que no busque en el Registro las bibliotecas de tipos.|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|Tiene la misma funcionalidad que el atributo [no_namespace](../preprocessor/no-namespace.md) pero se utiliza en las bibliotecas de tipos que se usan en la Directiva #import con el atributo [auto_search](../preprocessor/auto-search.md) .|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Suprime la creación de punteros inteligentes para todas las interfaces en la biblioteca de tipos.|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Indica al compilador que genere funciones contenedoras de bajo nivel para métodos y propiedades dispinterface que llaman a `IDispatch::Invoke` y devuelven el código de error HRESULT.|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Suprime la generación de funciones contenedoras de control de errores y declaraciones de [propiedad](../cpp/property-cpp.md) que utilizan esas funciones contenedoras.|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Especifica otro prefijo para evitar conflictos de nombres.|
|[raw_native_types](../preprocessor/raw-native-types.md)|Deshabilita el uso de las clases de soporte de COM en las funciones de contenedor de alto nivel y, en su lugar, fuerza el uso de tipos de datos de bajo nivel.|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Especifica los prefijos alternativos para tres métodos de propiedad.|
|[rename](../preprocessor/rename-hash-import.md)|Resuelve problemas del conflicto de nombres.|
|[rename_namespace](../preprocessor/rename-namespace.md)|Cambia el espacio de nombres que incluye el contenido de la biblioteca de tipos.|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|Tiene la misma funcionalidad que el atributo [rename_namespace](../preprocessor/rename-namespace.md) pero se utiliza en las bibliotecas de tipos que se usan en la Directiva #import con el atributo [auto_search](../preprocessor/auto-search.md) .|
|[tlbid](../preprocessor/tlbid.md)|Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
