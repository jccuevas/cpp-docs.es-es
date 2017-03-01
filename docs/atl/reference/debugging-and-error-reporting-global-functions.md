---
title: "Funciones globales de notificación de errores y depuración | Documentos de Microsoft"
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
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
caps.latest.revision: 17
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 4a412910d13d10606080c14412d33d2b614fdcec
ms.lasthandoff: 02/24/2017

---
# <a name="debugging-and-error-reporting-global-functions"></a>Funciones globales de notificación de errores y depuración
Estas funciones proporcionan útiles funciones de depuración y seguimiento.  
  
|||  
|-|-|  
|[AtlHresultFromLastError](http://msdn.microsoft.com/library/74530d7d-3c91-484c-acf3-aff755715d66)|Devuelve un `GetLastError` código de error en el formato HRESULT.|  
|[AtlHresultFromWin32](http://msdn.microsoft.com/library/63add2dd-274c-4e72-a98c-040b93413a2f)|Convierte un código de error Win32 en un valor HRESULT.|  
|[AtlReportError](http://msdn.microsoft.com/library/86b046a5-ea18-4ecf-9aab-40fc1eab847c)|Configura **IErrorInfo** para proporcionar detalles del error a un cliente.|  
|[AtlThrow](http://msdn.microsoft.com/library/2bd111da-8170-488d-914a-c9bf6b6765f7)|Produce una excepción `CAtlException`.|  
|[AtlThrowLastWin32](http://msdn.microsoft.com/library/8bce8e56-c7cd-4ebb-8c62-80ebc63a3d07)|Llame a esta función para notificar un error en función del resultado de la función de Windows `GetLastError`.|  
  
##  <a name="a-nameatlhresultfromlasterrora--atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a>AtlHresultFromLastError  
 Devuelve el último valor de código de error del subproceso que realiza la llamada con el formato HRESULT.  
  
```
HRESULT AtlHresultFromLastError();
```  
  
### <a name="remarks"></a>Comentarios  
 `AtlHresultFromLastError`llamadas `GetLastError` para obtener el último error y devuelve el error después de convertir en un valor HRESULT con el **error HRESULT_FROM_WIN32** macro.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcomcli.h  

##  <a name="a-nameatlhresultfromwin32a--atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a>AtlHresultFromWin32  
 Convierte un código de error Win32 en un valor HRESULT.  
  
```
AtlHresultFromWin32(DWORD error);
```  
  
### <a name="parameters"></a>Parámetros  
 *Error*  
 Para convertir el valor de error.  
  
### <a name="remarks"></a>Comentarios  
 Convierte un código de error de Win32 en un valor HRESULT, mediante la macro **error HRESULT_FROM_WIN32**.  
  
> [!NOTE]
>  En lugar de usar **HRESULT_FROM_WIN32(GetLastError())**, use la función [AtlHresultFromLastError](http://msdn.microsoft.com/library/74530d7d-3c91-484c-acf3-aff755715d66).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcomcli.h  

##  <a name="a-nameatlreporterrora--atlreporterror"></a><a name="atlreporterror"></a>AtlReportError  
 Configura el `IErrorInfo` interfaz para proporcionar información de error a los clientes del objeto.  
  
```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 [in] El CLSID del objeto que notifica el error.  
  
 `lpszDesc`  
 [in] Cadena que describe el error. Especifican las versiones de Unicode que `lpszDesc` es de tipo **LPCOLESTR**; la versión ANSI especifica un tipo de `LPCSTR`.  
  
 `iid`  
 [in] El IID de la interfaz que define el error o `GUID_NULL` si el error está definido por el sistema operativo.  
  
 `hRes`  
 [in] El `HRESULT` que desee devolver al llamador.  
  
 `nID`  
 [in] El identificador de recurso donde se almacena la cadena de descripción del error. Este valor debe estar comprendida entre 0 x 0200 y 0xFFFF, ambos inclusive. En compilaciones de depuración, una **ASSERT** se producirá si `nID` no indiza una cadena válida. En versiones de lanzamiento, la cadena de descripción del error se establecerá en "Error desconocido".  
  
 `dwHelpID`  
 [in] El identificador de contexto de ayuda para el error.  
  
 `lpszHelpFile`  
 [in] La ruta de acceso y el nombre del archivo de ayuda que describe el error.  
  
 `hInst`  
 [in] El identificador del recurso. De forma predeterminada, este parámetro es **__AtlBaseModuleModule::GetResourceInstance**, donde **__AtlBaseModuleModule** es la instancia global de [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) o una clase derivada de ella.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el `hRes` parámetro es distinto de cero, se devuelve el valor de `hRes`. Si `hRes` es cero, las primeras cuatro versiones de `AtlReportError` devolver `DISP_E_EXCEPTION`. Las dos últimas versiones devuelven el resultado de la macro **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.  
  
### <a name="remarks"></a>Comentarios  
 La cadena *lpszDesc* se utiliza como la descripción de texto del error. Cuando el cliente recibe la `hRes` devuelto desde `AtlReportError`, el cliente puede tener acceso a la **IErrorInfo** estructura para obtener más información sobre el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&52;](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]  
  
> [!CAUTION]
>  No utilice `AtlReportError` en C++ catch (controladores). Algunas invalidaciones de estas funciones utilizan las macros de conversión de cadena ATL internamente, que a su vez utiliza la `_alloca` función internamente. Mediante `AtlReportError` en un bloque catch de C++ controlador puede producir excepciones en los controladores catch de C++.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
    
##  <a name="a-nameatlthrowa--atlthrow"></a><a name="atlthrow"></a>AtlThrow  
 Llame a esta función para notificar un error en función de un código de estado `HRESULT`.  
  
```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```  
  
### <a name="parameters"></a>Parámetros  
 `hr`  
 Valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza por código de MFC y ATL en caso de una condición de error. También puede llamarse desde su propio código. La implementación predeterminada de esta función depende de la definición del símbolo **_ATL_NO_EXCEPTIONS** y el tipo de proyecto, MFC o ATL.  
  
 En todos los casos, esta función realiza un seguimiento el HRESULT al depurador.  
  
 En Visual Studio 2015 Update 3 y versiones posteriores, esta función es atributos __declspec (noreturn) para evitar advertencias falsas de SAL.  
  
 Si **_ATL_NO_EXCEPTIONS** no está definido en un proyecto MFC, esta función lanza una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o un [COleException](../../mfc/reference/coleexception-class.md) según el valor de HRESULT.  
  
 Si **_ATL_NO_EXCEPTIONS** no está definido en un proyecto ATL, la función se produce un [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Si **_ATL_NO_EXCEPTIONS** está definido, la función genera un error de aserción en lugar de producir una excepción.  
  
 Para los proyectos ATL, es posible proporcionar su propia implementación de esta función para usarse ATL en caso de error. Para ello, defina su propia función con la misma firma que `AtlThrow` y #define `AtlThrow` en el nombre de la función. Esto debe hacerse antes de incluir atlexcept.h (lo que significa que debe hacerse antes de incluir los encabezados ATL como atlbase.h incluye atlexcept.h). Atributo de la función `__declspec(noreturn)` para evitar advertencias falsas de SAL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#95;](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldef.h  

##  <a name="a-nameatlthrowlastwin32a--atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a>AtlThrowLastWin32  
 Llame a esta función para notificar un error en función del resultado de la función de Windows `GetLastError`.  
  
```
inline void AtlThrowLastWin32();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función realiza el seguimiento de los resultados de `GetLastError` al depurador.  
  
 Si **_ATL_NO_EXCEPTIONS** no está definido en un proyecto MFC, esta función lanza una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o un [COleException](../../mfc/reference/coleexception-class.md) basándose en el valor devuelto por `GetLastError`.  
  
 Si **_ATL_NO_EXCEPTIONS** no está definido en un proyecto ATL, la función se produce un [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Si **_ATL_NO_EXCEPTIONS** está definido, la función genera un error de aserción en lugar de producir una excepción.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldef.h  
   
     
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)   
 [Macros de informes de errores y depuración](../../atl/reference/debugging-and-error-reporting-macros.md)










