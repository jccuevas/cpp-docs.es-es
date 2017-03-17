---
title: Clase de CMonikerFile | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CMonikerFile class
- monikers, MFC
- IMoniker interface, binding
- IMoniker interface
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4668672af1b33170ece1cb4d449ed5a20f6040e7
ms.lasthandoff: 02/24/2017

---
# <a name="cmonikerfile-class"></a>Clase de CMonikerFile
Representa un flujo de datos ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)) llamado por un [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Construye un objeto `CMonikerFile`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMonikerFile::Close](#close)|Desasocia y libera la secuencia y libera el moniker.|  
|[CMonikerFile::Detach](#detach)|Desasocia el `IMoniker` de este `CMonikerFile` objeto.|  
|[CMonikerFile::GetMoniker](#getmoniker)|Devuelve el moniker actual.|  
|[CMonikerFile::Open](#open)|Abre el archivo especificado para obtener una secuencia.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|Obtiene el contexto de enlace o crea un contexto de enlace predeterminada inicializado.|  
  
## <a name="remarks"></a>Comentarios  
 Un moniker contiene información similar a una ruta de acceso a un archivo. Si tiene un puntero a un objeto moniker `IMoniker` interfaz, puede obtener acceso al archivo identificado sin necesidad de cualquier otra información específica sobre la ubicación del archivo realmente.  
  
 Deriva `COleStreamFile`, `CMonikerFile` toma un moniker o una representación de cadena puede convertir en un moniker y se enlaza a la secuencia para la que el moniker es un nombre. A continuación, puede leer y escribir en esa secuencia. El objetivo real de `CMonikerFile` es proporcionar un acceso sencillo a `IStream`s con el nombre `IMoniker`s por lo que no tiene que enlazar a una secuencia, aún tiene `CFile` funcionalidad en la secuencia.  
  
 `CMonikerFile`no se puede usar para enlazar a un valor distinto de una secuencia. Si desea enlazar a un objeto o de almacenamiento, debe utilizar el `IMoniker` directamente de interfaz.  
  
 Para obtener más información sobre secuencias y monikers, consulte [COleStreamFile](../../mfc/reference/colestreamfile-class.md) en el *referencia de MFC* y [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) y [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="close"></a>CMonikerFile::Close  
 Llame a esta función para separar y la versión de la secuencia y el moniker de la versión.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Se puede llamar en secuencias no abiertos o cerrados ya.  
  
##  <a name="cmonikerfile"></a>CMonikerFile::CMonikerFile  
 Construye un objeto `CMonikerFile`.  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>CMonikerFile::CreateBindContext  
 Llame a esta función para crear un contexto de enlace predeterminada inicializado.  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>Parámetros  
 `pError`  
 Un puntero a una excepción de archivo. En caso de error, se establecerá la causa del problema.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al contexto de enlace [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) para enlazar con si es correcto; en caso contrario **NULL**. Si la instancia se abrió con una `IBindHost` interfaz, se recupera el contexto de enlace de la `IBindHost`. Si no hay ningún `IBindHost` interfaz o la interfaz no puede devolver un contexto de enlace, se crea un contexto de enlace. Para obtener una descripción de la [IBindHost](http://msdn.microsoft.com/library/ie/ms775076) , vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Un contexto de enlace es un objeto que almacena información sobre una operación de enlace de moniker concreto. Puede reemplazar esta función para proporcionar un contexto de enlace personalizada.  
  
##  <a name="detach"></a>CMonikerFile::Detach  
 Llame a esta función para cerrar la secuencia.  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pError`  
 Un puntero a una excepción de archivo. En caso de error, se establecerá la causa del problema.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="getmoniker"></a>CMonikerFile::GetMoniker  
 Llame a esta función para recuperar un puntero para el moniker actual.  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la interfaz de moniker actual ( [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)).  
  
### <a name="remarks"></a>Comentarios  
 Puesto que `CMonikerFile` no es una interfaz, el puntero devuelto no incrementa el recuento de referencias (a través de [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)), y se libera el moniker cuando el `CMonikerFile` se libera el objeto. Si desea retener el moniker o liberar de usted mismo, debe `AddRef` .  
  
##  <a name="open"></a>CMonikerFile::Open  
 Llame a esta función miembro para abrir un objeto de archivo o el moniker.  
  
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
 Una dirección URL o el nombre del archivo que se va a abrir.  
  
 `pError`  
 Un puntero a una excepción de archivo. En caso de error, se establecerá la causa del problema.  
  
 `pMoniker`  
 Un puntero a la interfaz de moniker `IMoniker` que se usará para obtener una secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El `lpszURL` parámetro no puede utilizarse en un Macintosh. Sólo el `pMoniker` forma de **abiertos** puede utilizarse en un Macintosh.  
  
 Puede utilizar una dirección URL o un nombre de archivo para el `lpszURL` parámetro. Por ejemplo:  
  
 [!code-cpp[NVC_MFCWinInet Nº&6;](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 -O bien-  
  
 [!code-cpp[NVC_MFCWinInet&#7;](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase COleStreamFile](../../mfc/reference/colestreamfile-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

