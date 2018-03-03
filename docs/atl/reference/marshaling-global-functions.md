---
title: "Cálculo de referencias de funciones globales | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
dev_langs:
- C++
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a12f719d2cb893a5d2989a80f5fe09a5b49aeca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="marshaling-global-functions"></a>Cálculo de referencias de funciones globales
Estas funciones proporcionan compatibilidad para el cálculo de referencias y serialización de datos se convierte en punteros de interfaz.  
  
> [!IMPORTANT]
>  Las funciones se enumeran en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
|||  
|-|-|  
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Libera los datos de serialización y el `IStream` puntero.|  
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Crea un nuevo objeto de flujo y calcula las referencias del puntero de interfaz especificado.|  
|[AtlUnmarshalPtr](#atlunmarshalptr)|Convierte datos de serialización del flujo en un puntero de interfaz.|  

## <a name="requirements"></a>Requisitos:
**Encabezado:** atlbase.h
  
##  <a name="atlfreemarshalstream"></a>AtlFreeMarshalStream  
 Libera los datos de serializar del flujo; a continuación, libera el puntero del flujo.  

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 [in] Un puntero a la `IStream` interfaz en la secuencia que se usa para el cálculo de referencias.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
##  <a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc  
 Crea un nuevo objeto de flujo, escribe el CLSID del proxy en el flujo y calcula las referencias del puntero de interfaz especificado escribiendo los datos necesarios para inicializar el proxy en el flujo.  
  
```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Un puntero a la interfaz que se van a calcular.  
  
 `iid`  
 [in] El GUID de la interfaz que se va a serializar.  
  
 `ppStream`  
 [out] Un puntero a la `IStream` interfaz en el nuevo objeto de secuencia que se usan para serializar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 El **MSHLFLAGS_TABLESTRONG** marca se establece de modo que el puntero se puede serializar a varias secuencias. El puntero también se pueden deserializar varias veces.  
  
 Si se produce un error de la serialización, se libera el puntero del flujo.  
  
 `AtlMarshalPtrInProc`solo puede usarse en un puntero a un objeto en proceso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]  
  
##  <a name="atlunmarshalptr"></a>AtlUnmarshalPtr  
 Convierte los datos de serialización del flujo en un puntero de interfaz que puede usarse en el cliente.  
   
```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 [in] Un puntero a la secuencia que se resuelven referencias.  
  
 `iid`  
 [in] El GUID de la interfaz que se resuelven referencias.  
  
 `ppUnk`  
 [out] Un puntero a la interfaz deserializar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)
