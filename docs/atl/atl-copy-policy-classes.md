---
title: "ATL Copy Policy Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_Copy class"
  - "_CopyInterface class"
  - "clases [C++], copy policy"
  - "copy policy classes [C++]"
  - "datos [C++], ATL"
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ATL Copy Policy Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copie las clases de directivas son [clases de utilidad](../atl/utility-classes.md) utilizado para inicializar, copiar, eliminar datos.  Las clases de directivas de copia permiten definir la semántica de la copia para cualquier tipo de datos, y que define las conversiones entre los tipos de datos diferentes.  
  
 Las aplicaciones ATL copian clases de directiva en sus implementaciones de las plantillas siguientes:  
  
-   [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)  
  
-   [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)  
  
-   [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)  
  
 Encapsular la información necesaria para copiar o para convertir datos en una directiva de copia ordena que se puede pasar como argumento de plantilla, los desarrolladores de ATL ha previsto la reutilización extremo de estas clases.  Por ejemplo, si necesita implementar una colección con cualquier tipo de datos arbitrario, todo lo que necesita proporcionar es la directiva adecuada de copia; no es necesario que el código que implementa la colección.  
  
## Definición  
 Por definición, una clase que proporciona funciones estáticas siguientes es una clase de directiva de copia:  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 Puede reemplazar los tipos `DestinationType` y *SourceType* con tipos de datos arbitrarios para cada directiva de copia.  
  
> [!NOTE]
>  Aunque puede definir directivas de copia ordena para los tipos de datos arbitrarios, el uso de las clases de código ATL debe limitar los tipos que tienen sentido.  Por ejemplo, al utilizar una clase de directiva de copia con las implementaciones de colección o de enumerador ATL, `DestinationType` debe ser un tipo que se puede utilizar como un parámetro en un método de interfaz COM.  
  
 Utilice **init** para inicializar los datos, **copy** para copiar datos, y **destroy** para liberar los datos.  El significado exacto de inicialización, la copia, y destrucción son el dominio de la clase de directiva de copia y variarán en función de los tipos de datos implicados.  
  
 Hay dos requisitos en el uso y la implementación de una clase de directiva de copia:  
  
-   El primer parámetro a **copy** debe recibir solo un puntero a los datos que ha inicializado previamente mediante **init**.  
  
-   **destroy** debe recibir solo nunca un puntero a los datos que ha inicializado previamente mediante **init** copiado o mediante **copy**.  
  
## Implementaciones estándar  
 ATL proporciona dos tipos de directivas de copia en forma de clases de plantilla de **\_Copy** y de **\_CopyInterface** :  
  
-   La clase de **\_Copy** permite copiar homogéneo \(no conversión entre los tipos de datos\) ya que proporciona un solo parámetro de plantilla para especificar `DestinationType` y *SourceType*.  La implementación genérica de esta plantilla no contiene ninguna inicialización o código de destrucción y utiliza `memcpy` para copiar los datos.  ATL también proporciona especializaciones de **\_Copy** para **VARIANT**, `LPOLESTR`, los tipos de datos **OLEVERB**, y de **CONNECTDATA** .  
  
-   La clase de **\_CopyInterface** proporciona una implementación para copiar punteros de interfaz después de reglas COM estándar.  Esta clase permite de nuevo sólo copiar homogéneo, usa una asignación simple y una llamada a `AddRef` para realizar la copia.  
  
## Implementaciones personalizadas  
 Normalmente, necesitará definir sus propias clases de directivas de copia para copiar heterogéneo \(es decir, conversión entre los tipos de datos\).  Para algunos ejemplos de clases de directivas de copia personalizadas, vea los archivos VCUE\_Copy.h y VCUE\_CopyString.h en el ejemplo de [ATLCollections](../top/visual-cpp-samples.md) .  Estos archivos contienen dos clases de directivas de copia de la plantilla, `GenericCopy` y `MapCopy`, más varias especializaciones de `GenericCopy` para los tipos de datos diferentes.  
  
### GenericCopy  
 `GenericCopy` permite especificar *SourceType* y `DestinationType` como argumentos de plantilla.  Ésta es la forma más general de la clase de `GenericCopy` de VCUE\_Copy.h:  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/CPP/atl-copy-policy-classes_1.h)]  
  
 VCUE\_Copy.h también contiene las especializaciones siguientes de esta clase: `GenericCopy<BSTR>`, `GenericCopy<VARIANT, BSTR>`, `GenericCopy<BSTR, VARIANT>`.  VCUE\_CopyString.h contiene las especializaciones copiado de s para **std::string**: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, y `GenericCopy<BSTR, std::string>`.  Puede mejorar `GenericCopy` proporcionando otras especializaciones propios.  
  
### MapCopy  
 `MapCopy` supone que los datos que se copian se almacenan en un mapa de STL\- estilo, por lo que permiten especificar el tipo de mapa donde se almacenan los datos y el tipo de destino.  La implementación de la clase simplemente utiliza tipos proporcionados por la clase *de MapType* para determinar el tipo de datos de origen y llamar a la clase correspondiente de `GenericCopy` .  No hay especializaciones de esta clase necesarias.  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/CPP/atl-copy-policy-classes_2.h)]  
  
## Vea también  
 [Implementing an STL\-Based Collection](../atl/implementing-an-stl-based-collection.md)   
 [Ejemplo ATLCollections](../top/visual-cpp-samples.md)