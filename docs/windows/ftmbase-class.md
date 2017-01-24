---
title: "FtmBase (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FtmBase (clase)"
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un objeto libre\- con el contador.  
  
## Sintaxis  
  
```  
  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags< WinRtClassicComMix >,   
   Microsoft::WRL::CloakedIid< IMarshal > >;  
```  
  
## Comentarios  
 Para obtener más información, vea el tema “IMarshal” en el subtema “las interfaces COM” del tema de “referencia COM” en MSDN Library.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[FtmBase::FtmBase \(Constructor\)](../windows/ftmbase-ftmbase-constructor.md)|Inicializa una nueva instancia de la clase de FtmBase.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable \(Método\)](../windows/ftmbase-createglobalinterfacetable-method.md)|Crea una tabla global \(GIT\) de interfaz.|  
|[FtmBase::DisconnectObject \(Método\)](../windows/ftmbase-disconnectobject-method.md)|Fuertemente libera todos conexiones externas a un objeto.  El servidor del objeto llama a la implementación de este método antes del cierre.|  
|[FtmBase::GetMarshalSizeMax \(Método\)](../windows/ftmbase-getmarshalsizemax-method.md)|Obtiene el límite superior en el número de bytes necesarios para formar el puntero de interfaz especificado en el objeto especificado.|  
|[FtmBase::GetUnmarshalClass \(Método\)](../windows/ftmbase-getunmarshalclass-method.md)|Obtiene el CLSID que utiliza COM para encontrar un archivo DLL que contiene el código para el proxy correspondiente.  COM carga esta DLL para crear una instancia no inicializada del proxy.|  
|[FtmBase::MarshalInterface \(Método\)](../Topic/FtmBase::MarshalInterface%20Method.md)|Escribe en una secuencia los datos necesarios para inicializar un objeto proxy en un proceso de cliente.|  
|[FtmBase::ReleaseMarshalData \(Método\)](../Topic/FtmBase::ReleaseMarshalData%20Method.md)|Destruye un paquete de datos formado.|  
|[FtmBase::UnmarshalInterface \(Método\)](../windows/ftmbase-unmarshalinterface-method.md)|Inicializa un proxy creado recientemente y devuelve un puntero de interfaz a ese proxy.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[FtmBase::marshaller\_ \(Miembro de datos\)](../windows/ftmbase-marshaller-data-member.md)|Contiene una referencia al contador de subproceso libre.|  
  
## Jerarquía de herencia  
 `FtmBase`  
  
## Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)