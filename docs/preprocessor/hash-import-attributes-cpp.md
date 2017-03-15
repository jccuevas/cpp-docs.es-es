---
title: "#import (Atributos) (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#import (directiva), atributos"
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #import (Atributos) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona vínculos a los atributos utilizados con la directiva \#import.  
  
 **Específicos de Microsoft**  
  
 Los atributos siguientes están disponibles para la directiva \#import.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|[auto\_rename](../preprocessor/auto-rename.md)|Cambia de nombre las palabras reservadas de C\+\+ al anexar dos caracteres de subrayado \(\_\_\) al nombre de la variable para resolver posibles conflictos de nombre.|  
|[auto\_search](../preprocessor/auto-search.md)|Especifica que, cuando se hace referencia a una biblioteca de tipos mediante \#import y ella misma hace referencia a otra biblioteca de tipos, el compilador puede realizar un \#import implícito para la otra biblioteca de tipos.|  
|[embedded\_idl](../preprocessor/embedded-idl.md)|Especifica que la biblioteca de tipos se escriba en el archivo .tlh, conservando el código generado por el atributo.|  
|[exclude](../preprocessor/exclude-hash-import.md)|Excluye elementos de los archivos de encabezado de la biblioteca de tipos que se generan.|  
|[high\_method\_prefix](../preprocessor/high-method-prefix.md)|Especifica un prefijo que se utilizará para designar propiedades y métodos de alto nivel.|  
|[high\_property\_prefixes](../preprocessor/high-property-prefixes.md)|Especifica los prefijos alternativos para tres métodos de propiedad.|  
|[implementation\_only](../preprocessor/implementation-only.md)|Suprime la generación de archivos de encabezado .tlh \(el archivo de encabezado principal\).|  
|[include\(\)](../preprocessor/include-parens.md)|Deshabilita la exclusión automática.|  
|[inject\_statement](../preprocessor/inject-statement.md)|Inserta el argumento como texto original en el encabezado de la biblioteca de tipos.|  
|[named\_guids](../preprocessor/named-guids.md)|Indica al compilador que defina e inicialice las variables GUID antiguas con el formato **LIBID\_MyLib**, **CLSID\_MyCoClass**, **IID\_MyInterface** y **DIID\_MyDispInterface**.|  
|[no\_auto\_exclude](../preprocessor/no-auto-exclude.md)|Deshabilita la exclusión automática.|  
|[no\_dual\_interfaces](../preprocessor/no-dual-interfaces.md)|Cambia la manera en que el compilador genera las funciones de contenedor para los métodos de interfaz dual.|  
|[no\_implementation](../preprocessor/no-implementation.md)|Suprime la generación del encabezado .tli, que contiene las implementaciones de las funciones miembro de contenedor.|  
|[no\_namespace](../preprocessor/no-namespace.md)|Especifica que el compilador no genera el espacio de nombres.|  
|[no\_registry](../preprocessor/no-registry.md)|Indica al compilador que no busque en el Registro las bibliotecas de tipos.|  
|[no\_search\_namespace](../preprocessor/no-search-namespace.md)|Tiene la misma funcionalidad que el atributo [no\_namespace](../preprocessor/no-namespace.md), pero se utiliza en las bibliotecas de tipos que se usan la directiva \#import con el atributo [auto\_search](../preprocessor/auto-search.md).|  
|[no\_smart\_pointers](../preprocessor/no-smart-pointers.md)|Suprime la creación de punteros inteligentes para todas las interfaces en la biblioteca de tipos.|  
|[raw\_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Indica al compilador que genere funciones de contenedor de bajo nivel para los métodos y propiedades dispinterface que llamen a **IDispatch::Invoke** y devuelvan el código de error `HRESULT`.|  
|[raw\_interfaces\_only](../preprocessor/raw-interfaces-only.md)|Suprime la generación de funciones de contenedor para control de errores y las declaraciones [propiedad](../cpp/property-cpp.md) que utilizan esas funciones de contenedor.|  
|[raw\_method\_prefix](../preprocessor/raw-method-prefix.md)|Especifica otro prefijo para evitar conflictos de nombres.|  
|[raw\_native\_types](../preprocessor/raw-native-types.md)|Deshabilita el uso de las clases de soporte de COM en las funciones de contenedor de alto nivel y, en su lugar, fuerza el uso de tipos de datos de bajo nivel.|  
|[raw\_property\_prefixes](../preprocessor/raw-property-prefixes.md)|Especifica los prefijos alternativos para tres métodos de propiedad.|  
|[rename](../preprocessor/rename-hash-import.md)|Resuelve problemas del conflicto de nombres.|  
|[rename\_namespace](../preprocessor/rename-namespace.md)|Cambia el espacio de nombres que incluye el contenido de la biblioteca de tipos.|  
|[rename\_search\_namespace](../preprocessor/rename-search-namespace.md)|Tiene la misma funcionalidad que el atributo [rename\_namespace](../preprocessor/rename-namespace.md), pero se utiliza en las bibliotecas de tipos que se usan la directiva \#import con el atributo [auto\_search](../preprocessor/auto-search.md).|  
|[tlbid](../preprocessor/tlbid.md)|Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.|  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)