---
title: "Serializaci&#243;n (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET Framework [C++], serialización"
  - "código administrado [C++], serializar"
  - "NonSerializedAttribute (clase), aplicaciones administradas"
  - "SerializableAttribute (clase), aplicaciones administradas"
  - "serialización [C++]"
  - "serialización [C++], acerca de la serialización"
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Serializaci&#243;n (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La serialización \(proceso de almacenar el estado de un objeto o un miembro en un soporte permanente\) de las clases administradas \(incluyendo campos y propiedades individuales\) es compatible con las clases <xref:System.SerializableAttribute> y <xref:System.NonSerializedAttribute>.  
  
## Comentarios  
 El atributo personalizado **SerializableAttribute** se aplica a una clase administrada para serializar la clase completa o solamente a campos o propiedades particulares para serializarla parcialmente.  El atributo personalizado **NonSerializedAttribute** se emplea para excluir de la serialización campos o propiedades concretos de una clase administrada.  
  
## Ejemplo  
  
### Descripción  
 En el ejemplo siguiente, la clase `MyClass` \(y la propiedad `m_nCount`\) se marca como serializable.  No obstante, la propiedad `m_nData` no se serializa, como así lo indica el atributo personalizado **NonSerialized**:  
  
### Código  
  
```  
// serialization_and_mcpp.cpp  
// compile with: /LD /clr  
using namespace System;  
  
[ Serializable ]  
public ref class MyClass {  
public:  
   int m_nCount;  
private:  
   [ NonSerialized ]  
   int m_nData;  
};  
```  
  
### Comentarios  
 Observe que se puede hacer referencia a los dos atributos utilizando su "nombre corto" \(**Serializable** y **NonSerialized**\).  Puede obtener una explicación más pormenorizada en [Aplicar atributos](../Topic/Applying%20Attributes.md).  
  
## Vea también  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)