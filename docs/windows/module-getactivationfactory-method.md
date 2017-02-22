---
title: "Module::GetActivationFactory (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::GetActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetActivationFactory (método)"
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Module::GetActivationFactory (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene una fábrica de activación para el módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW HRESULT GetActivationFactory(  
   _In_ HSTRING pActivatibleClassId,  
   _Deref_out_ IActivationFactory **ppIFactory,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pActivatibleClassId`  
 IID de una clase en tiempo de ejecución.  
  
 `ppIFactory`  
 IActivationFactory para la clase en tiempo de ejecución.  
  
 `serverName`  
 El nombre de un subconjunto de los generadores de clases en el módulo actual. Especifique el nombre del servidor usado en el [ActivatableClassWithFactoryEx](../Topic/ActivatableClass%20Macros.md) (macro), o especificar `nullptr` para obtener el nombre del servidor predeterminado.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, el valor HRESULT devuelto por GetActivationFactory.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
[Clase de módulo](../windows/module-class.md)
 [ActivatableClass (Macros)](../Topic/ActivatableClass%20Macros.md)