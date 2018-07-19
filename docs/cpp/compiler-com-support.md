---
title: Compatibilidad con COM del compilador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a21b7dd00aa0bb0894da4cc13cf0f6f40078ee1b
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941832"
---
# <a name="compiler-com-support"></a>Compatibilidad con COM del compilador
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 El compilador de Visual C++ puede leer directamente bibliotecas de tipos de modelo de objetos componentes (COM) y traducir el contenido a código fuente de C++ que se puede incluir en la compilación. Existen extensiones de lenguaje disponibles para facilitar la programación COM en el cliente.  
  
 Mediante el uso de la [directiva de preprocesador #import](../preprocessor/hash-import-directive-cpp.md), el compilador puede leer una biblioteca de tipos y convertir las interfaces en un archivo de encabezado de C++ que describe el COM como clases. Existe un conjunto de atributos `#import` disponible para el control por parte del usuario del contenido de los archivos de encabezado de biblioteca de tipos resultantes.  
  
 Puede usar el [__declspec](../cpp/declspec.md) atributo extendido [uuid](../cpp/uuid-cpp.md) para asignar un identificador único global (GUID) a un objeto COM. La palabra clave [__uuidof](../cpp/uuidof-operator.md) puede utilizarse para extraer el GUID asociado a un objeto COM. Otro `__declspec` atributo, [propiedad](../cpp/property-cpp.md), puede utilizarse para especificar el **obtener** y **establecer** métodos para un miembro de datos de un objeto COM.  
  
 Se proporciona un conjunto de clases y funciones globales de soporte técnico de COM para admitir la `VARIANT` y `BSTR` tipos, implementar punteros inteligentes y encapsular el objeto de error iniciado por `_com_raise_error`:  
  
-   [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)  
  
-   [_bstr_t](../cpp/bstr-t-class.md)  
  
-   [_com_error](../cpp/com-error-class.md)  
  
-   [_com_ptr_t](../cpp/com-ptr-t-class.md)  
  
-   [_variant_t](../cpp/variant-t-class.md)  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)   
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)