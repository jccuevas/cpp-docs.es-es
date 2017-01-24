---
title: "ComPtr (Clase) | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtr (clase)"
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. ComPtr mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.  
  
## Sintaxis  
  
```  
template <  
   typename T  
>  
class ComPtr;  
  
template<  
   class U  
>  
friend class ComPtr;  
```  
  
#### Parámetros  
 `T`  
 La interfaz que la clase ComPtr representa.  
  
 `U`  
 Una clase para la que ComPtr es de confianza. \(La plantilla que usa este parámetro está protegida\).  
  
## Comentarios  
 ComPtr\<\> declara un tipo que representa el puntero de interfaz subyacente. Use ComPtr\<\> para declarar una variable y luego use el operador de acceso a miembros de flecha \(`->`\) para tener acceso a una función miembro de interfaz.  
  
 Para obtener más información sobre los punteros inteligentes, consulte la subsección "Punteros inteligentes de COM" del tema [COM Coding Practices](http://msdn.microsoft.com/es-es/76aca556-b4d6-4e67-a2a3-4439900f0c39) en MSDN Library.  
  
## Miembros  
  
### Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`InterfaceType`|Un sinónimo del tipo especificado por el parámetro de plantilla `T`.|  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[ComPtr::ComPtr \(Constructor\)](../windows/comptr-comptr-constructor.md)|Inicializa una nueva instancia de la clase ComPtr. Las sobrecargas proporcionan constructores predeterminados, así como de copia, movimiento y conversión.|  
|[ComPtr::~ComPtr \(Destructor\)](../windows/comptr-tilde-comptr-destructor.md)|Desinicializa una instancia de ComPtr.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[ComPtr::As \(Método\)](../windows/comptr-as-method.md)|Devuelve un objeto de ComPtr que representa la interfaz identificada por el parámetro de plantilla especificado.|  
|[ComPtr::AsIID \(Método\)](../windows/comptr-asiid-method.md)|Devuelve un objeto de ComPtr que representa la interfaz identificada por el identificador de plantilla especificado.|  
|[ComPtr::AsWeak \(Método\)](../windows/comptr-asweak-method.md)|Recupera una referencia débil al objeto actual.|  
|[ComPtr::Attach \(Método\)](../windows/comptr-attach-method.md)|Asocia esta clase ComPtr con el tipo de interfaz especificado por el parámetro de tipo de plantilla actual.|  
|[ComPtr::CopyTo \(Método\)](../windows/comptr-copyto-method.md)|Copia la interfaz actual o especificada asociada a esta ComPtr al puntero de salida especificado.|  
|[ComPtr::Detach \(Método\)](../Topic/ComPtr::Detach%20Method.md)|Desasocia esta ComPtr de la interfaz que representa.|  
|[ComPtr::Get \(Método\)](../windows/comptr-get-method.md)|Recupera un puntero a la interfaz que está asociada a esta ComPtr.|  
|[ComPtr::GetAddressOf \(Método\)](../Topic/ComPtr::GetAddressOf%20Method.md)|Recupera la dirección del miembro de datos [ptr\_](../windows/comptr-ptr-data-member.md) que contiene un puntero a la interfaz representada por esta ComPtr.|  
|[ComPtr::ReleaseAndGetAddressOf \(Método\)](../windows/comptr-releaseandgetaddressof-method.md)|Libera la interfaz asociada a esta ComPtr y después recupera la dirección del miembro de datos [ptr\_](../windows/comptr-ptr-data-member.md), que contiene un puntero a la interfaz que se liberó.|  
|[ComPtr::Reset](../windows/comptr-reset.md)|Libera todas las referencias del puntero a la interfaz asociada a este ComPtr.|  
|[ComPtr::Swap \(Método\)](../windows/comptr-swap-method.md)|Intercambia la interfaz administrada por la clase ComPtr actual con la interfaz administrada por la ComPtr especificada.|  
  
### Métodos protegidos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[ComPtr::InternalAddRef \(Método\)](../windows/comptr-internaladdref-method.md)|Incrementa el recuento de referencias de la interfaz asociada a esta ComPtr.|  
|[ComPtr::InternalRelease \(Método\)](../windows/comptr-internalrelease-method.md)|Realiza una operación de liberación de COM en la interfaz asociada a esta ComPtr.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[ComPtr::operator Microsoft::WRL::Details::BoolType \(Operador\)](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|Indica si una ComPtr administra o no la duración del objeto de una interfaz.|  
|[ComPtr::operator& \(Operador\)](../windows/comptr-operator-ampersand-operator.md)|Recupera la dirección de la ComPtr actual.|  
|[ComPtr::operator\= \(Operador\)](../windows/comptr-operator-assign-operator.md)|Asigna un valor a la ComPtr actual.|  
|[ComPtr::operator\-\> \(Operador\)](../windows/comptr-operator-arrow-operator.md)|Recupera un puntero al tipo especificado por el parámetro de plantilla actual.|  
|[ComPtr::operator\=\= \(Operador\)](../windows/comptr-operator-equality-operator.md)|Indica si dos objetos de ComPtr son iguales.|  
|[ComPtr::operator\!\= \(Operador\)](../windows/comptr-operator-inequality-operator.md)|Indica si dos objetos de ComPtr son diferentes.|  
  
### Miembros de datos protegidos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[ComPtr::ptr\_ \(Miembro de datos\)](../windows/comptr-ptr-data-member.md)|Contiene un puntero a la interfaz que está asociad y está administrado por esta ComPtr.|  
  
## Jerarquía de herencia  
 `ComPtr`  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)