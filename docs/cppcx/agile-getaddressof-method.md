---
title: "Agile::GetAddressOf (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::GetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::GetAddressOf"
ms.assetid: f015edf9-4155-4992-a6fc-7ff1edcc5d1e
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::GetAddressOf (M&#233;todo)
Reinicializa el objeto Agile actual y luego devuelve la dirección de un identificador a un objeto de tipo `T`.  
  
## Sintaxis  
  
```cpp  
  
       T^* GetAddressOf()   
throw();  
```  
  
#### Parámetros  
 `T`  
 Un tipo especificado por el parámetro typename de la plantilla.  
  
## Valor devuelto  
 Dirección de un identificador para un objeto de tipo `T`.  
  
## Comentarios  
 Esta operación libera la representación actual de un objeto de tipo `T`, en caso de haberlo; reinicializa los miembros de datos del objeto Agile; adquiere el contexto de subprocesos actual; y luego devuelve la dirección de una variable de controlador a objeto que puede representar un objeto que no es Agile. Para hacer que una instancia de la clase Agile represente un objeto, use el operador de asignación \([Agile::operator\=](../cppcx/agile-operator-assign-operator.md)\) para asignar el objeto a la instancia de la clase Agile.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Agile \(Clase\)](../cppcx/platform-agile-class.md)