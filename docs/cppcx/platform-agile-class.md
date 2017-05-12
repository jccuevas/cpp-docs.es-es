---
title: "Platform::Agile (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile"
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Agile (Clase)
Representa un objeto que tiene MashalingBehavior\=Standard como objeto ágil, lo que reduce en gran medida las posibilidades de excepciones de subprocesamiento en tiempo de ejecución.`Agile<T>` permite que el objeto que no es Agile llame al mismo subproceso o a otro diferente, o que le llame a él. Para obtener más información, consulta [Subprocesamiento y cálculo de referencias](../cppcx/threading-and-marshaling-c-cx.md).  
  
## Sintaxis  
  
```scr  
  
template <typename T>  
    class Agile  
;  
```  
  
#### Parámetros  
 T  
 typename de la clase que no es Agile.  
  
## Comentarios  
 La mayoría de las clases de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] son Agile. Un objeto Agile puede llamar a un objeto en proceso o fuera de proceso del mismo subproceso u otro diferente, o que le llame a él. Si un objeto no es Agile, ajuste el objeto que no Agile en un objeto `Agile<T>`, que es Agile. Se pueden calcular las referencias del objeto `Agile<T>` y se puede usar el objeto que no es Agile subyacente.  
  
 La clase `Agile<T>` es una clase de C\+\+ estándar, nativa y requiere `agile.h`. Representa el objeto que no es Agile y el *contexto* del objeto Agile. El contexto especifica el modelo de subprocesos de un objeto Agile y el comportamiento del cálculo de referencias. El sistema operativo usa el contexto para determinar de qué manera calcular las referencias de un objeto.  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Agile::Agile \(Constructor\)](../cppcx/agile-agile-constructor.md)|Inicializa una nueva instancia de la clase Agile.|  
|[Agile::~Agile \(Destructor\)](../cppcx/agile-tilde-agile-destructor.md)|Destruye la instancia actual de la clase Agile.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Agile::Get](../cppcx/agile-get-method.md)|Devuelve un identificador al objeto representado por el objeto Agile actual.|  
|[Agile::GetAddressOf](../cppcx/agile-getaddressof-method.md)|Reinicializa el objeto Agile actual y luego devuelve la dirección de un identificador a un objeto de tipo `T`.|  
|[Agile::GetAddressOfForInOut](../cppcx/agile-getaddressofforinout-method.md)|Devuelve la dirección de un identificador al objeto representado por el objeto Agile actual.|  
|[Agile::Release](../cppcx/agile-release-method.md)|Descarta el objeto y el contexto subyacentes del objeto Agile actual.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Agile::operator\-\>](../cppcx/agile-operator-arrow-operator.md)|Recupera un identificador al objeto representado por el objeto Agile actual.|  
|[Agile::operator\=](../cppcx/agile-operator-assign-operator.md)|Asigna el valor especificado al objeto Agile actual.|  
  
## Jerarquía de herencia  
 `Object`  
  
 `Agile`  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** agile.h  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)