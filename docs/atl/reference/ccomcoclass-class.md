---
title: Clase CComCoClass | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCoClass
- ATL.CComCoClass
- ATL::CComCoClass
dev_langs:
- C++
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6201051a38ac65788086dcf7ee4c3f3441988e71
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcoclass-class"></a>CComCoClass (clase)
Esta clase proporciona métodos para crear instancias de una clase y obtener sus propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, const CLSID* pclsid = &CLSID_NULL>  
class CComCoClass
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `CComCoClass`.  
  
 *pTypeInfo*  
 Puntero al CLSID del objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComCoClass:: CreateInstance](#createinstance)|(Estático) Crea una instancia de la clase y las consultas de una interfaz.|  
|[CComCoClass::Error](#error)|(Estático) Devuelve información de error enriquecida para el cliente.|  
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Estático) Devuelve el identificador de clase.|  
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Estático) Invalidar para devolver la descripción del objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComCoClass`Proporciona métodos para recuperar el CLSID de un objeto, establecer información de error y crear instancias de la clase. Cualquier clase registrada en el [mapa de objetos](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f) debe derivar de `CComCoClass`.  
  
 `CComCoClass`También define el modelo de fábrica y agregación de clase predeterminado para el objeto. `CComCoClass`utiliza las dos macros siguientes:  
  
- [DECLARE_CLASSFACTORY](http://msdn.microsoft.com/library/51a6b925-07c0-4d3a-9174-0b8c808975e4) declara el generador de clases que [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).  
  
- [DECLARE_AGGREGATABLE](http://msdn.microsoft.com/library/e7e568d7-04e0-4226-b5dc-224deed229ab) declara que puede agregarse el objeto.  
  
 Puede invalidar cualquiera de estos valores predeterminados especificando otra macro en su definición de clase. Por ejemplo, para usar [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) en lugar de `CComClassFactory`, especifique el [macro DECLARE_CLASSFACTORY2](http://msdn.microsoft.com/library/38a6c969-7297-4bb1-9ba6-1fe2d355b285) macro:  
  
 [!code-cpp[NVC_ATL_COM&#2;](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-namecreateinstancea--ccomcoclasscreateinstance"></a><a name="createinstance"></a>CComCoClass:: CreateInstance  
 Utilice estos `CreateInstance` funciones para crear una instancia de COM de un objeto y recuperar un puntero de interfaz sin usar la API de COM.  
  
```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 `Q`  
 La interfaz COM que debe devolverse a través de `pp`.  
  
 *punkOuter*  
 [in] El desconocido externo o desconocido de control del agregado.  
  
 `pp`  
 [out] La dirección de una variable de puntero que recibe el puntero de interfaz solicitada si se crea correctamente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar. Consulte [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una descripción de los posibles valores devueltos.  
  
### <a name="remarks"></a>Comentarios  
 Usar la primera sobrecarga de esta función para la creación de objeto típico; usar la segunda sobrecarga cuando necesita agregar el objeto que se va a crear.  
  
 La clase implementa el objeto COM necesario (es decir, la clase que se utiliza como el primer parámetro de plantilla [CComCoClass](../../atl/reference/ccomcoclass-class.md)) debe estar en el mismo proyecto que el código de llamada. La creación del objeto COM se lleva a cabo por el generador de clases registrado para esta clase ATL.  
  
 Estas funciones son útiles para crear objetos que han impide externamente puede crear utilizando el [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](http://msdn.microsoft.com/library/abdc093c-6502-42de-8419-b7ebf45299d1) macro. También son útiles en situaciones donde desea evitar la API de COM, por motivos de eficacia.  
  
 Tenga en cuenta que la interfaz `Q` debe tener un IID asociado que se puede recuperar mediante el [__uuidof](../../cpp/uuidof-operator.md) operador.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, `CDocument` se deriva de una clase ATL generados por el asistente `CComCoClass` que implementa el **IDocument** interfaz. La clase se registra en el mapa de objetos con la `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO` (macro), por lo que los clientes pueden crear instancias de documento mediante [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615). `CApplication`es una coclase que proporciona un método en una de sus propias interfaces COM para crear instancias de la clase de documento. El código siguiente muestra lo fácil que crear instancias de la clase de documento con el `CreateInstance` miembro heredado de la `CComCoClass` clase base.  
  
 [!code-cpp[NVC_ATL_COM&#11;](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]  
  
##  <a name="a-nameerrora--ccomcoclasserror"></a><a name="error"></a>CComCoClass::Error  
 Esta función estática se configura el `IErrorInfo` interfaz para proporcionar información de error al cliente.  
  
```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszDesc`  
 [in] Cadena que describe el error. La versión Unicode de `Error` especifica que `lpszDesc` es de tipo **LPCOLESTR**; la versión ANSI especifica un tipo de `LPCSTR`.  
  
 `iid`  
 [in] El IID de la interfaz que define el error o `GUID_NULL` (el valor predeterminado) si el error está definido por el sistema operativo.  
  
 `hRes`  
 [in] El `HRESULT` que desee devolver al llamador. El valor predeterminado es 0. Para obtener más información sobre `hRes`, vea la sección Comentarios.  
  
 `nID`  
 [in] El identificador de recurso donde se almacena la cadena de descripción del error. Este valor debe estar comprendida entre 0 x 0200 y 0xFFFF, ambos inclusive. En compilaciones de depuración, una **ASSERT** se producirá si `nID` no indiza una cadena válida. En versiones de lanzamiento, la cadena de descripción del error se establecerá en "Error desconocido".  
  
 `dwHelpID`  
 [in] El identificador de contexto de ayuda para el error.  
  
 `lpszHelpFile`  
 [in] La ruta de acceso y el nombre del archivo de ayuda que describe el error.  
  
 `hInst`  
 [in] El identificador del recurso. De forma predeterminada, este parámetro es **_AtlModule::GetResourceInstance**, donde **_AtlModule** es la instancia global de [CAtlModule](../../atl/reference/catlmodule-class.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar. Para conocer más detalles, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a `Error`, el objeto debe implementar la `ISupportErrorInfo Interface` interfaz.  
  
 Si el `hRes` parámetro es distinto de cero, a continuación, `Error` devuelve el valor de `hRes`. Si `hRes` es cero, las primeras cuatro versiones de `Error` devolver `DISP_E_EXCEPTION`. Las dos últimas versiones devuelven el resultado de la macro **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.  
  
##  <a name="a-namegetobjectclsida--ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a>CComCoClass::GetObjectCLSID  
 Proporciona una manera coherente de recuperar el CLSID del objeto.  
  
```
static const CLSID& WINAPI GetObjectCLSID();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de clase del objeto.  
  
##  <a name="a-namegetobjectdescriptiona--ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a>CComCoClass::GetObjectDescription  
 Esta función estática recupera la descripción de texto para el objeto class.  
  
```
static LPCTSTR WINAPI GetObjectDescription();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Descripción del objeto de clase.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada devuelve **NULL**. Puede invalidar este método con la [DECLARE_OBJECT_DESCRIPTION](http://msdn.microsoft.com/library/32ac881c-97b1-44e2-a017-0e23eb99ac93) (macro). Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM&#12;](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]  
  
 `GetObjectDescription`llama a **IComponentRegistrar::GetComponents**. **IComponentRegistrar** es una interfaz de automatización que le permite registrar y anular el registro de componentes individuales en un archivo DLL. Cuando se crea un objeto de registro del componente con el Asistente para proyectos ATL, el Asistente implementará automáticamente el **IComponentRegistrar** interfaz. **IComponentRegistrar** se utiliza normalmente con Microsoft Transaction Server.  
  
 Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

