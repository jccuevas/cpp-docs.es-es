---
title: Clase de CMonikerFile | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
dev_langs:
- C++
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 431e743396cfc22d49c13a2a9e2f50c88c5ee036
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369234"
---
# <a name="cmonikerfile-class"></a>Clase de CMonikerFile
Representa un flujo de datos ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)) con el nombre por un [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Construye un objeto `CMonikerFile`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonikerFile::Close](#close)|Desasocia y libera el flujo y libera el moniker.|  
|[CMonikerFile::Detach](#detach)|Desasocia el `IMoniker` desde este `CMonikerFile` objeto.|  
|[CMonikerFile::GetMoniker](#getmoniker)|Devuelve el moniker actual.|  
|[CMonikerFile::Open](#open)|Abre el archivo especificado para obtener una secuencia.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|Obtiene el contexto de enlace o crea un contexto de enlace inicializado de forma predeterminada.|  
  
## <a name="remarks"></a>Comentarios  
 Un moniker contiene información de forma muy similar a una ruta de acceso a un archivo. Si tiene un puntero a un objeto moniker `IMoniker` interfaz, puede obtener acceso al archivo identificado sin necesidad de cualquier otra información específica sobre la ubicación del archivo realmente.  
  
 Deriva `COleStreamFile`, `CMonikerFile` toma un moniker o una representación de cadena puede convertir en un moniker y se enlaza a la secuencia para la que el moniker es un nombre. A continuación, puede leer y escribir en esa secuencia. El propósito real de `CMonikerFile` es proporcionar un acceso sencillo a `IStream`s con el nombre `IMoniker`para que no es necesario que enlazar a una secuencia usted mismo, aún tienen `CFile` funcionalidad a la secuencia.  
  
 `CMonikerFile` no puede utilizarse para enlazar a algo distinto de una secuencia. Si desea enlazar a un objeto o de almacenamiento, debe utilizar el `IMoniker` interfaz directamente.  
  
 Para obtener más información sobre secuencias y monikers, consulte [COleStreamFile](../../mfc/reference/colestreamfile-class.md) en el *referencia de MFC* y [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) y [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) en el SDK de Windows.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="close"></a>  CMonikerFile::Close  
 Llame a esta función de adjuntar y separar la versión de la secuencia y el moniker de la versión.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Se puede llamar en secuencias no abiertos o cerrados ya.  
  
##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile  
 Construye un objeto `CMonikerFile`.  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext  
 Llame a esta función para crear un contexto de enlace inicializado de forma predeterminada.  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>Parámetros  
 `pError`  
 Un puntero a una excepción de archivo. Si se produce un error, se establecerá la causa.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al contexto de enlace [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) para enlazar con si es correcto; en caso contrario **NULL**. Si la instancia se abrió con una `IBindHost` interfaz, el contexto de enlace se recupera de la `IBindHost`. Si no hay ningún `IBindHost` interfaz o la interfaz no puede devolver un contexto de enlace, se crea un contexto de enlace. Para obtener una descripción de la [IBindHost](http://msdn.microsoft.com/library/ie/ms775076) de la interfaz, vea el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Un contexto de enlace es un objeto que almacena información sobre una operación de enlace de moniker determinado. Puede invalidar esta función para proporcionar un contexto de enlace personalizada.  
  
##  <a name="detach"></a>  CMonikerFile::Detach  
 Llame a esta función para cerrar la secuencia.  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pError`  
 Un puntero a una excepción de archivo. Si se produce un error, se establecerá la causa.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker  
 Llame a esta función para recuperar un puntero para el moniker actual.  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la interfaz de moniker actual ( [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)).  
  
### <a name="remarks"></a>Comentarios  
 Puesto que `CMonikerFile` no es una interfaz, el puntero devuelto no incrementa el recuento de referencias (a través de [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)), y el moniker se libera cuando el `CMonikerFile` se libera el objeto. Si desea retener el moniker o de la versión usted mismo, debe `AddRef` .  
  
##  <a name="open"></a>  CMonikerFile::Open  
 Llame a esta función miembro para abrir un objeto de archivo o moniker.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszURL,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    IMoniker* pMoniker,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszURL`  
 Una dirección URL o el nombre de archivo del archivo que se puede abrir.  
  
 `pError`  
 Un puntero a una excepción de archivo. Si se produce un error, se establecerá la causa.  
  
 `pMoniker`  
 Un puntero a la interfaz de moniker `IMoniker` que se usará para obtener un flujo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszURL` parámetro no se puede usar en un equipo Macintosh. Solo el `pMoniker` forma de **abiertos** se puede usar en un equipo Macintosh.  
  
 Puede usar una dirección URL o un nombre de archivo para el `lpszURL` parámetro. Por ejemplo:  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 - O  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase COleStreamFile](../../mfc/reference/colestreamfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile (clase)](../../mfc/reference/casyncmonikerfile-class.md)
