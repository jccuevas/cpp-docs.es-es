---
title: '#importar los atributos (C++)'
ms.date: 11/04/2016
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: 954dfec50db75c0e3d11f0924b0ee398cd211fe1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036145"
---
# <a name="import-attributes-c"></a>#import (Atributos) (C++)
Proporciona vínculos a los atributos utilizados con el `#import` directiva.

**Específicos de Microsoft**

Los siguientes atributos están disponibles para el `#import` directiva.

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
|[named_guids](../preprocessor/named-guids.md)|Indica al compilador que defina e inicialice las variables GUID en estilo antiguo, el formato `LIBID_MyLib`, `CLSID_MyCoClass`, `IID_MyInterface`, y `DIID_MyDispInterface`.|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Deshabilita la exclusión automática.|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Cambia la manera en que el compilador genera las funciones de contenedor para los métodos de interfaz dual.|
|[no_implementation](../preprocessor/no-implementation.md)|Suprime la generación del encabezado .tli, que contiene las implementaciones de las funciones miembro de contenedor.|
|[no_namespace](../preprocessor/no-namespace.md)|Especifica que el compilador no genera el espacio de nombres.|
|[no_registry](../preprocessor/no-registry.md)|Indica al compilador que no busque en el Registro las bibliotecas de tipos.|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|Tiene la misma funcionalidad que el [no_namespace](../preprocessor/no-namespace.md) atributo pero se usa en las bibliotecas de tipos que usan la directiva #import con el [auto_search](../preprocessor/auto-search.md) atributo.|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Suprime la creación de punteros inteligentes para todas las interfaces en la biblioteca de tipos.|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Indica al compilador que genere funciones de contenedor de bajo nivel para dispinterface métodos y propiedades que llaman a `IDispatch::Invoke` y devolver el código de error HRESULT.|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Suprime la generación de funciones de contenedor de control de errores y [propiedad](../cpp/property-cpp.md) declaraciones que utilizan esas funciones de contenedor.|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Especifica otro prefijo para evitar conflictos de nombres.|
|[raw_native_types](../preprocessor/raw-native-types.md)|Deshabilita el uso de las clases de soporte de COM en las funciones de contenedor de alto nivel y, en su lugar, fuerza el uso de tipos de datos de bajo nivel.|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Especifica los prefijos alternativos para tres métodos de propiedad.|
|[rename](../preprocessor/rename-hash-import.md)|Resuelve problemas del conflicto de nombres.|
|[rename_namespace](../preprocessor/rename-namespace.md)|Cambia el espacio de nombres que incluye el contenido de la biblioteca de tipos.|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|Tiene la misma funcionalidad que el [rename_namespace](../preprocessor/rename-namespace.md) atributo pero se usa en las bibliotecas de tipos que usan la directiva #import con el [auto_search](../preprocessor/auto-search.md) atributo.|
|[tlbid](../preprocessor/tlbid.md)|Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)