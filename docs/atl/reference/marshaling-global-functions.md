---
title: "Cálculo de referencias de funciones globales | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: dd4b8d50ec69974b7b2af29438b1657e1ce592b4
ms.lasthandoff: 02/24/2017

---
# <a name="marshaling-global-functions"></a>Cálculo de referencias de funciones globales
Estas funciones proporcionan compatibilidad para el cálculo de referencias y conversión de datos de cálculo de referencias a punteros de interfaz.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Libera los datos de cálculo y el `IStream` puntero.|  
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Crea un nuevo objeto de secuencia y calcula las referencias del puntero de interfaz especificado.|  
|[AtlUnmarshalPtr](#atlunmarshalptr)|Convierte datos de cálculo de referencias de la secuencia en un puntero de interfaz.|  
  
##  <a name="a-nameatlfreemarshalstreama--atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream  
 Libera los datos de serializar del flujo; a continuación, libera el puntero del flujo.  

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 [in] Un puntero a la `IStream` interfaz en la secuencia utilizada para el cálculo de referencias.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
##  <a name="a-nameatlmarshalptrinproca--atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc  
 Crea un nuevo objeto de flujo, escribe el CLSID del proxy en el flujo y calcula las referencias del puntero de interfaz especificado escribiendo los datos necesarios para inicializar el proxy en el flujo.  
  
```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Puntero a la interfaz que se van a calcular.  
  
 `iid`  
 [in] El GUID de la interfaz que se calculan las referencias.  
  
 `ppStream`  
 [out] Un puntero a la `IStream` interfaz en el nuevo objeto de secuencia utilizado para el cálculo de referencias.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 El **MSHLFLAGS_TABLESTRONG** marca está establecida para el puntero se puede calcular referencias a varias secuencias. El puntero también se puede deserializar varias veces.  
  
 Si se produce un error de cálculo de referencias, se libera el puntero de la secuencia.  
  
 `AtlMarshalPtrInProc`sólo puede utilizarse en un puntero a un objeto en proceso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM Nº&50;](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]  
  
##  <a name="a-nameatlunmarshalptra--atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr  
 Convierte los datos de serialización del flujo en un puntero de interfaz que puede usarse en el cliente.  
   
```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 [in] Puntero a la secuencia que se resuelven referencias.  
  
 `iid`  
 [in] El GUID de la interfaz que se resuelven referencias.  
  
 `ppUnk`  
 [out] Puntero a la interfaz deserializan.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)

