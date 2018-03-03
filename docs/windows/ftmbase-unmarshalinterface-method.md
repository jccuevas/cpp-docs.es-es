---
title: "Ftmbase:: UnmarshalInterface (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- UnmarshalInterface method
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce3710e84a9f7680b56f461029f279a659a5c14a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface (Método)
Inicializa a un proxy recién creado y devuelve un puntero de interfaz a ese proxy.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStm`  
 Puntero a la secuencia desde la que se puede deserializar el puntero de interfaz.  
  
 `riid`  
 Referencia al identificador de la interfaz que puede deserializar.  
  
 `ppv`  
 Cuando se completa esta operación, la dirección de una variable de puntero que recibe el puntero de interfaz solicitado en `riid`. Si esta operación se realiza correctamente, *`ppv` contiene el puntero de interfaz solicitada de la interfaz que puede deserializar.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_NOINTERFACE o E_FAIL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [FtmBase (clase)](../windows/ftmbase-class.md)