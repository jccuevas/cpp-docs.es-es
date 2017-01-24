---
title: "Implementation of a Custom String Manager (Advanced Method) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlStringMgr class, utilizar"
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementation of a Custom String Manager (Advanced Method)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En situaciones especializadas, puede que desee implementar un administrador de cadena personalizado que hace más que el cambio que la pila se utiliza para asignar memoria.  En esta situación, debe implementar manualmente la interfaz de [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) como administrador de cadena personalizado.  
  
 Para ello, es importante que primero entender cómo [CStringT](../atl-mfc-shared/reference/cstringt-class.md) utiliza esa interfaz para administrar los datos de cadena.  cada instancia de `CStringT` tiene un puntero a una estructura de [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) .  Esta estructura de longitud variable contiene información importante sobre la cadena \(como longitud\), así como datos de caracteres reales para la cadena.  Cada administrador de cadena personalizado es responsable de asignar y de liberar estas estructuras a solicitud de `CStringT`.  
  
 La estructura de `CStringData` incluye cuatro campos:  
  
-   Puntos del campo de[pStringMgr](../Topic/CStringData::pStringMgr.md) This a la interfaz de `IAtlStringMgr` utilizada para administrar estos datos de cadena.  Cuando `CStringT` necesita reasignar o liberar el búfer de cadena que llama a los métodos de Reallocate o Free de esta interfaz, pasando la estructura de `CStringData` como parámetro.  Al asignar una estructura de `CStringData` en el administrador de la cadena, debe establecer este campo para notificar al administrador de cadena personalizado.  
  
-   El campo de[nDataLength](../Topic/CStringData::nDataLength.md) This contiene la longitud lógica actual de la cadena almacenada en el búfer excepto la null final.  `CStringT` actualiza este campo cuando la longitud de la cadena.  Al asignar una estructura de `CStringData` , el administrador de la cadena debería establecer este campo a cero.  Al reasignar una estructura de `CStringData` , el administrador de cadena personalizado debe dejar este campo sin cambios.  
  
-   El campo de[nAllocLength](../Topic/CStringData::nAllocLength.md) This contiene el número máximo de caracteres \(excepto la null final\) que se puede almacenar en este búfer de cadena sin reasignación de.  Siempre que `CStringT` necesite aumentar el intervalo lógica de la cadena, comprueba primero este campo para asegurarse de que hay suficiente espacio en el búfer.  Si se produce un error en la comprobación, las llamadas de `CStringT` en el administrador de cadena personalizado para reasignar el búfer.  Cuando asignar o la reasignación de una estructura de `CStringData` , debe establecer este campo al menos el número de caracteres solicitado en el parámetro de **nChars** a [IAtlStringMgr:: Asigna](../Topic/IAtlStringMgr::Allocate.md) o a [IAtlStringMgr:: reasigne](../Topic/IAtlStringMgr::Reallocate.md).  Si hay más espacio en el búfer que solicitado, puede establecer este valor para reflejar la cantidad de espacio real disponible.  Esto permite que `CStringT` aumenta la cadena para rellenar el espacio asignado completo antes de que tenga que devolver en el administrador de la cadena para reasignar el búfer.  
  
-   El campo de[nRefs](../Topic/CStringData::nRefs.md) This contiene el recuento actual de la referencia del búfer de cadena.  Si el valor es uno, entonces una única instancia de `CStringT` utiliza el búfer.  Además, la instancia se permite a leer y modificar el contenido del búfer.  Si el valor es mayor que uno, varias instancias de `CStringT` pueden utilizar el búfer.  Dado que se comparte el búfer de caracteres, las instancias de `CStringT` pueden leer sólo el contenido del búfer.  Para modificar el contenido, `CStringT` primero hace una copia del búfer.  Si el valor es negativo, solo una instancia de `CStringT` utiliza el búfer.  en este caso, el búfer se considera bloqueado.  Cuando una instancia de `CStringT` utiliza un búfer bloqueado ningún otras instancias de `CStringT` pueden compartir el búfer.  En su lugar, estas instancias crean una copia del búfer antes de manipular el contenido.  Además, la instancia de `CStringT` utilizando el búfer bloqueado no intenta compartir el búfer de ninguna otra instancia de `CStringT` asignada a ella.  en este caso, la instancia de `CStringT` copia la otra cadena en el búfer bloqueado.  
  
     Al asignar una estructura de `CStringData` , debe establecer este campo para reflejar el tipo de uso compartido está permitido para el búfer.  Para la mayoría de las implementaciones, establezca este valor en uno.  Esto permite el comportamiento habitual de la copia\-en\-escritura.  Sin embargo, si el administrador de la cadena no admite compartir el búfer de cadena, establezca este campo a un estado bloqueado.  Esto obliga a `CStringT` para usar este búfer para la instancia de `CStringT` que lo asignada.  
  
## Vea también  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)