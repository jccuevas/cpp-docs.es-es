---
title: "pair (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::pair"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pair (clase) [STL/CLR]"
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# pair (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que contenga un par de valores.  
  
## Sintaxis  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### Parámetros  
 Value1  
 El tipo de primer valor ajustado.  
  
 Value2  
 El tipo de segundo valor ajustado.  
  
## Miembros  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|[pair::first\_type](../dotnet/pair-first-type-stl-clr.md)|El tipo del primer valor ajustado.|  
|[pair::second\_type](../dotnet/pair-second-type-stl-clr.md)|El tipo del segundo valor ajustado.|  
  
|Objeto miembro|Descripción|  
|--------------------|-----------------|  
|[pair::first](../dotnet/pair-first-stl-clr.md)|El primer valor almacenado.|  
|[pair::second](../dotnet/pair-second-stl-clr.md)|El segundo valor almacenado.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[pair::pair](../dotnet/pair-pair-stl-clr.md)|Construye un objeto de pares.|  
|[pair::swap](../dotnet/pair-swap-stl-clr.md)|Cambia el contenido de dos pares.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[pair::operator\=](../dotnet/pair-operator-assign-stl-clr.md)|Reemplaza los pares almacenados de valores.|  
  
## Comentarios  
 El objeto almacena un par de valores.  Utiliza esta clase de plantilla para combinar dos valores en un único objeto.  Observe que `cliext::pair` \(descrito aquí\) almacena sólo tipos administrados; para almacenar un par de tipos no administrados utilice `std::pair`, declarado en `<utility>`.  
  
## Requisitos  
 cliext \<\/utilidad de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [make\_pair](../dotnet/make-pair-stl-clr.md)