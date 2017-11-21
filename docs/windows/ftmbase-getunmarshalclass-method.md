---
title: "Ftmbase:: GetUnmarshalClass (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs: C++
helpviewer_keywords: GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 967c8e8cc397a7f9efdb145bf337049627f24a2c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass (Método)
Obtiene el CLSID que utiliza COM para encontrar el archivo DLL que contiene el código para el proxy correspondiente. COM carga este archivo DLL para crear una instancia no inicializada del proxy.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 Referencia al identificador de la interfaz que se van a calcular.  
  
 `pv`  
 Puntero a la interfaz que se van a calcular; puede ser NULL si el llamador no tiene un puntero a la interfaz deseada.  
  
 `dwDestContext`  
 Contexto de destino donde se puede deserializar la interfaz especificada.  
  
 Especifique uno o varios valores de enumeración de MSHCTX.  
  
 Puede producirse la resolución de referencias en otro contenedor del proceso actual (MSHCTX_INPROC) o en otro proceso en el mismo equipo que el proceso actual (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Reservado para uso futuro; debe ser NULL.  
  
 `mshlflags`  
 Cuando se completa esta operación, puntero al CLSID que se usará para crear un proxy en el proceso del cliente.  
  
 `pCid`  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, S_FALSE.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [FtmBase (clase)](../windows/ftmbase-class.md)