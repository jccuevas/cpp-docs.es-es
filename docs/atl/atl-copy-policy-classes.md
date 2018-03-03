---
title: Clases de directiva de copia de ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54ac3c9d53c3b6d2b295643001fd15b1e4c6c46d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-copy-policy-classes"></a>Clases de directiva de copia de ATL
Las clases de directiva de copia son [las clases de utilidad](../atl/utility-classes.md) utilizado para inicializar, copiar y eliminar datos. Clases de directivas de copia permiten definir semánticas de copia para cualquier tipo de datos, así como definir conversiones entre tipos de datos diferentes.  
  
 ATL utiliza clases de directivas de copia en sus implementaciones de las siguientes plantillas:  
  
-   [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)  
  
-   [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)  
  
-   [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)  
  
 Al encapsular la información necesaria para copiar o convertir datos en una clase de directiva de copia que se puede pasar como argumento de plantilla, los programadores de ATL han proporcionado para ser reutilizada extreme de estas clases. Por ejemplo, si necesita implementar una colección con cualquier tipo de datos arbitrarios, todo lo que necesita para proporcionar es la directiva de copia apropiada; nunca tendrá que modificar el código que implementa la colección.  
  
## <a name="definition"></a>Definición  
 Por definición, una clase que proporciona las siguientes funciones estáticas es una clase de directiva de copia:  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 Puede reemplazar los tipos de `DestinationType` y *SourceType* con tipos de datos arbitrarios para cada directiva de copia.  
  
> [!NOTE]
>  Aunque puede definir clases de directivas de copia para cualquier tipo de datos arbitrarios, debe limitar el uso de las clases en código ATL los tipos que tengan sentido. Por ejemplo, si mediante una directiva de copia la clase con la colección de ATL o implementaciones de enumerador, `DestinationType` debe ser un tipo que puede usarse como un parámetro en un método de interfaz COM.  
  
 Use **init** para inicializar datos, **copia** para copiar los datos, y **destruir** para liberar los datos. El significado exacto de inicialización, copiar y destrucción están en el dominio de la clase de directiva de copia y variarán según los tipos de datos implicados.  
  
 Hay dos requisitos sobre el uso y la implementación de una clase de directiva de copia:  
  
-   El primer parámetro **copia** solo se debe recibir un puntero a datos que previamente ha inicializado con **init**.  
  
-   **destruir** siempre se debe recibir un puntero a datos que previamente ha inicializado con **init** o copiar a través de **copia**.  
  
## <a name="standard-implementations"></a>Implementaciones estándar  
 ATL proporciona dos clases de directivas de copia en el formulario de la **_Copy** y **_CopyInterface** clases de plantilla:  
  
-   El **_Copy** clase permite sólo admite copias homogénea (no conversión entre tipos de datos) ya que sólo ofrece un parámetro de plantilla único para especificar tanto `DestinationType` y *SourceType*. La implementación genérica de esta plantilla no contiene ningún código de inicialización o de destrucción y usa `memcpy` para copiar los datos. ATL también ofrece especializaciones de **_Copy** para **VARIANT**, `LPOLESTR`, **OLEVERB**, y **CONNECTDATA** tipos de datos.  
  
-   El **_CopyInterface** clase proporciona una implementación para copiar punteros de interfaz que siguen reglas COM estándar. Una vez más esta clase permite solo copiar homogéneos, por lo que utiliza la asignación simple y una llamada a `AddRef` para realizar la copia.  
  
## <a name="custom-implementations"></a>Implementaciones personalizadas  
 Normalmente, necesitará definir sus propias clases de directiva de copia para copias heterogéneas (es decir, la conversión entre tipos de datos). Algunos ejemplos de clases de directivas de copia personalizadas, examine los archivos VCUE_Copy.h y VCUE_CopyString.h en el [ATLCollections](../visual-cpp-samples.md) ejemplo. Estos archivos contienen dos clases de directiva de copia de plantilla, `GenericCopy` y `MapCopy`, junto con un número de especializaciones de `GenericCopy` para distintos tipos de datos.  
  
### <a name="genericcopy"></a>GenericCopy  
 `GenericCopy`le permite especificar el *SourceType* y `DestinationType` como argumentos de plantilla. Esta es la forma más general de la `GenericCopy` clase a partir de VCUE_Copy.h:  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]  
  
 VCUE_Copy.h también contiene las siguientes especializaciones de esta clase: `GenericCopy<BSTR>`, `GenericCopy<VARIANT, BSTR>`, `GenericCopy<BSTR, VARIANT>`. VCUE_CopyString.h contiene especializaciones para copiar desde **std:: String**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, y `GenericCopy<BSTR, std::string>`. Se podría mejorar `GenericCopy` aportando posteriores especializaciones de su propia.  
  
### <a name="mapcopy"></a>MapCopy  
 `MapCopy`se da por supuesto que los datos copiados se almacenan en un mapa de estilo de biblioteca estándar de C++, por lo que permite especificar el tipo de mapa en el que se almacenan los datos y el tipo de destino. La implementación de la clase solo utiliza las definiciones de tipo proporcionado por el *MapType* (clase) para determinar el tipo del origen de datos y llamar a la correspondiente `GenericCopy` clase. No se necesitan ningún especializaciones de esta clase.  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]  
  
## <a name="see-also"></a>Vea también  
 [Implementación de una colección de basada en la biblioteca estándar de C++](../atl/implementing-an-stl-based-collection.md)   
 [Ejemplo ATLCollections](../visual-cpp-samples.md)

