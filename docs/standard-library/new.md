---
title: '&lt;new&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <new>
dev_langs: C++
helpviewer_keywords: new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 263c6ec455c55492425617d2ffee499655a727dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ltnewgt"></a>&lt;new&gt;
Define varios tipos y funciones que controlan la asignación y liberación de almacenamiento bajo el control del programa. También define los componentes para la creación de informes de errores de administración de almacenamiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <new>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Algunas de las funciones declaradas en este encabezado son reemplazables. La implementación proporciona una versión predeterminada, cuyo comportamiento se describe en este documento. No obstante, un programa puede definir una función con la misma firma para reemplazar la versión predeterminada en tiempo de vinculación. La versión de reemplazo debe cumplir los requisitos descritos en este documento.  
  
### <a name="objects"></a>de la empresa  
  
|||  
|-|-|  
|[nothrow](../standard-library/new-functions.md#nothrow)|Proporciona un objeto que se usará como argumento para las versiones `nothrow` de **new** y **delete**.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Tipo que apunta a una función que se puede usar como un nuevo controlador.|  
  
### <a name="functions"></a>Funciones  
  
|||  
|-|-|  
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Instala una función de usuario que se llama cuando el nuevo controlador no puede asignar memoria.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator delete](../standard-library/new-operators.md#op_delete)|Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para objetos individuales.|  
|[operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Función a la que llama una expresión delete para cancelar la asignación de almacenamiento para una matriz de objetos.|  
|[operator new](../standard-library/new-operators.md#op_new)|Función a la que llama una expresión new para asignar el almacenamiento para objetos individuales.|  
|[operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Función a la que llama una expresión new para asignar el almacenamiento para una matriz de objetos.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[bad_alloc Class](../standard-library/bad-alloc-class.md)|Clase que describe una excepción que se produce para indicar que una solicitud de asignación no se realizó correctamente.|  
|[nothrow_t Class](../standard-library/nothrow-t-structure.md)|Clase que se usa como parámetro de función del operador new para indicar que la función debe devolver un puntero nulo para notificar un error de asignación, en lugar de producir una excepción.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



