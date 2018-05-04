---
title: Interfaz IRegistrar | Documentos de Microsoft
ms.custom: ''
ms.date: 2/1/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
dev_langs:
- C++
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89d1e9269536ee28f2c8dd29819ff594c89c186b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="iregistrar-interface"></a>Interfaz IRegistrar
Esta interfaz se define en atliface.h y se usa internamente las funciones de miembro de CAtlModule como [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).   
  
## <a name="syntax"></a>Sintaxis  
  
```
typedef interface IRegistrar IRegistrar;
```  
## <a name="remarks"></a>Comentarios
Vea el tema [utilizar parámetros reemplazables (el preprocesador del registrador)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) para obtener más detalles.  

## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Registra el recurso. |  
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Anula el registro del recurso.|  
|[IRegistrar::FileRegister](#fileregister)|Registra el archivo.|  
|[IRegistrar::FileUnregister](#fileunregister)|Anula el registro del archivo.|  
|[IRegistrar::StringRegister](#stringregister)|Registra la cadena.|  
|[IRegistrar::StringUnregister](#stringunregister)|Anula el registro de la cadena|  
|[IRegistrar::ResourceRegister](#resourceregister)|Registra el recurso.|  
|[IRegistrar::ResourceUnregister](#resourceunregister)|Anula el registro del recurso.| 
  

 
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlifase.h  
  
##  <a name="resourceregistersz"></a>  IRegistrar::ResourceRegisterSz 
 Registra el recurso.  
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
  
 
  
##  <a name="resourceunregistersz"></a>  IRegistrar::ResourceUnregisterSz  
 Anula el registro del recurso.
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
  
  
##  <a name="fileregister"></a>  IRegistrar::FileRegister  
Registra el archivo.
  
```
virtual HRESULT STDMETHODCALLTYPE FileRegister( 
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```  
  
  
##  <a name="fileunregister"></a>  IRegistrar::FileUnregister  
Anula el registro del archivo.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister( 
    */ _In_z_ LPCOLESTR fileName) = 0;
```  
  
 
##  <a name="stringregister"></a>  IRegistrar::StringRegister  
  Registra los datos de cadena especificada.
```
virtual HRESULT STDMETHODCALLTYPE StringRegister( 
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```  
  
##  <a name="stringunregister"></a>  IRegistrar::StringUnregister
 Anula el registro de los datos de cadena especificada.  
  
```
virtualHRESULT STDMETHODCALLTYPE StringUnregister( 
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```  

  
##  <a name="resourceregister"></a>  IRegistrar::ResourceRegister  
 Registra el recurso.  
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
   
  
##  <a name="resourceunregister"></a>  IRegistrar::ResourceUnregister  
 Anula el registro del recurso.  
  
```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0; 
```  
 
## <a name="see-also"></a>Vea también  
 [Usar parámetros reemplazables (el preprocesador del registrador)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)   
 [Componente de registro (registrador)](../../atl/atl-registry-component-registrar.md)  
