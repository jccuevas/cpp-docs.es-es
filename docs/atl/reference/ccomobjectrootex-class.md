---
title: CComObjectRootEx (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComObjectRootEx
- ATL::CComObjectRootEx<ThreadModel>
- CComObjectRootEx
- ATL::CComObjectRootEx
- ATL.CComObjectRootEx<ThreadModel>
dev_langs:
- C++
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
caps.latest.revision: 20
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f3a6d26ddb4f612824f959ca3046531dc3bbf2a9
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx (clase)
Esta clase proporciona métodos para controlar la administración de recuento de referencia de objeto para objetos agregados y de agregado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class ThreadModel>  
class CComObjectRootEx : public CComObjectRootBase
```  
  
#### <a name="parameters"></a>Parámetros  
 `ThreadModel`  
 La clase cuyos métodos de implementan el modelo de subprocesos deseado. Puede elegir el modelo de subprocesamiento estableciendo explícitamente `ThreadModel` a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), o [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Puede aceptar el modelo de subprocesos predeterminado del servidor estableciendo `ThreadModel` a [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) o [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).  

  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CComObjectRootEx](#ccomobjectrootex)|Constructor.|  
|[InternalAddRef](#internaladdref)|Incrementa el recuento de referencias para un objeto no agregado.|  
|[InternalRelease](#internalrelease)|Disminuye el recuento de referencias para un objeto no agregado.|  
|[Bloqueo](#lock)|Si el modelo de subprocesos es multiproceso, obtiene la propiedad de un objeto de sección crítica.|  
|[Desbloquear](#unlock)|Si el modelo de subprocesos es multiproceso, libera la posesión de un objeto de sección crítica.|  
  
### <a name="ccomobjectrootbase-methods"></a>Métodos de CComObjectRootBase  
  
|||  
|-|-|  
|[FinalConstruct](#finalconstruct)|Reemplazar en la clase para realizar cualquier inicialización requerida por el objeto.|  
|[FinalRelease](#finalrelease)|Reemplazar en la clase para realizar cualquier limpieza requerida por el objeto.|  
|[OuterAddRef](#outeraddref)|Incrementa el recuento de referencias para un objeto agregado.|  
|[OuterQueryInterface](#outerqueryinterface)|Delega en el exterior **IUnknown** de un objeto agregado.|  
|[OuterRelease](#outerrelease)|Disminuye el recuento de referencias para un objeto agregado.|  
  
### <a name="static-functions"></a>Funciones estáticas  
  
|||  
|-|-|  
|[InternalQueryInterface](#internalqueryinterface)|Delega en el **IUnknown** de un objeto no agregado.|  
|[ObjectMain](#objectmain)|Llamado durante la inicialización del módulo y finalización para las clases derivadas que se muestran en el mapa de objetos.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_dwRef](#m_dwref)|Con `m_pOuterUnknown`, que forma parte de una unión. Usar cuando el objeto no se agrega para contener el recuento de referencias de `AddRef` y **versión**.|  
|[m_pOuterUnknown](#m_pouterunknown)|Con `m_dwRef`, que forma parte de una unión. Se utiliza cuando se agrega el objeto para almacenar un puntero para el desconocido externo.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObjectRootEx`controla la administración de recuento de referencia de objeto para objetos agregados y agregados. Contiene el recuento de referencias de objeto si el objeto no se agrega y mantiene el puntero para el desconocido externo si se agrega el objeto. Objetos agregados, `CComObjectRootEx` métodos pueden utilizarse para controlar los errores del objeto interno para construir y proteger el objeto externo de eliminación cuando se publican las interfaces internas o el objeto interno se elimina.  
  
 Una clase que implementa un servidor COM debe heredar de `CComObjectRootEx` o [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).  
  
 Si la definición de clase especifica la [DECLARE_POLY_AGGREGATABLE](http://msdn.microsoft.com/library/7569e738-cfbc-4404-ba1d-78dcefa3bdb3) (macro), ATL crea una instancia de **CComPolyObject\<CSuClase >** cuando **IClassFactory:: CreateInstance** se llama. Durante la creación, se comprueba el valor del objeto desconocido externo. Si es **NULL**, **IUnknown** se implementa para un objeto no agregado. Si el desconocido externo no es **NULL**, **IUnknown** se implementa para un objeto agregado.  
  
 Si no especifica la clase de la `DECLARE_POLY_AGGREGATABLE` (macro), ATL crea una instancia de **CAggComObject\<CSuClase >** para objetos agregados o una instancia de **CComObject\<CSuClase >** sin agregar objetos.  
  
 La ventaja de usar `CComPolyObject` es evitar tener ambos `CComAggObject` y `CComObject` en su módulo para controlar los casos agregados y no agregados. Una sola `CComPolyObject` objeto controla ambos casos. Por lo tanto, sólo una copia de la tabla vtable y una copia de las funciones existe en el módulo. Si su tabla vtable es grande, puede reducir sustancialmente el tamaño del módulo. Sin embargo, si su tabla vtable es pequeña, usando `CComPolyObject` puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, como son `CComAggObject` y `CComObject`.  
  
 Si se agrega el objeto, [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) implementa `CComAggObject` o `CComPolyObject`. Estas clases delegación `QueryInterface`, `AddRef`, y **versión** llama a `CComObjectRootEx`de `OuterQueryInterface`, `OuterAddRef`, y `OuterRelease` para reenviar el desconocido externo. Normalmente, invalidar `CComObjectRootEx::FinalConstruct` en su clase para crear objetos agregados y reemplace `CComObjectRootEx::FinalRelease` liberarlos agrega objetos.  
  
 Si el objeto no es agregado, **IUnknown** implementa `CComObject` o `CComPolyObject`. En este caso, se llama a `QueryInterface`, `AddRef`, y **versión** se delegan a `CComObjectRootEx`de `InternalQueryInterface`, `InternalAddRef`, y `InternalRelease` para realizar las operaciones reales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-nameccomobjectrootexa--ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a>CComObjectRootEx::CComObjectRootEx  
 El constructor inicializa el recuento de referencias en 0.  
  
```
CComObjectRootEx();
```  
  
##  <a name="a-namefinalconstructa--ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a>CComObjectRootEx::FinalConstruct  
 Puede invalidar este método en una clase derivada para realizar cualquier inicialización necesaria para el objeto.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver `S_OK` éxito o un error estándar `HRESULT` valores.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `CComObjectRootEx::FinalConstruct` simplemente devuelve `S_OK`.  
  
 Hay ventajas para realizar la inicialización en `FinalConstruct` en lugar del constructor de la clase:  
  
-   No puede devolver un código de estado de un constructor, pero puede devolver una `HRESULT` por medio de `FinalConstruct`del valor devuelto. Cuando se crean los objetos de la clase utilizando el generador de clases estándar proporcionado por ATL, este valor devuelto se propaga hacia el cliente COM, lo que le permite proporcionar información detallada del error.  
  
-   No se puede llamar a funciones virtuales a través del mecanismo de función virtual desde el constructor de una clase. Llamar a una función virtual desde el constructor de una clase produce una llamada a la función resuelto estáticamente según se define en ese momento en la jerarquía de herencia. Llamadas a funciones virtuales puras como resultado errores del vinculador.  
  
     La clase no es la clase más derivada en la jerarquía de herencia, que se basa en una clase derivada proporcionada por ATL para proporcionar parte de su funcionalidad. Hay muy probable que la inicialización será necesario usar las características proporcionadas por esa clase (Esto es especialmente cierto cuando los objetos de la clase necesitan otros objetos de agregado), pero el constructor de la clase no tiene forma de obtener acceso a esas características. El código de construcción de la clase se ejecuta antes de que se haya construido totalmente la clase más derivada.  
  
     Sin embargo, `FinalConstruct` se llama inmediatamente después de que la mayoría deriva se haya construido totalmente clase que permite llamar a funciones virtuales y usar la implementación de recuento de referencias proporcionada por ATL.  
  
### <a name="example"></a>Ejemplo  
 Normalmente, invalide este método en la clase derivada de `CComObjectRootEx` crear agregan objetos. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM Nº&40;](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]  
  
 Si se produce un error en la construcción, puede devolver un error. También puede utilizar la macro [macro DECLARE_PROTECT_FINAL_CONSTRUCT](http://msdn.microsoft.com/library/2d2e5ddc-057a-43ca-87c8-d3477a8193a0) impedir que el objeto externo está eliminado si, durante la creación, el objeto agregado interno incrementa el recuento de referencias, a continuación, disminuye el recuento de 0.  
  
 Aquí es una forma habitual de crear un agregado:  
  
-   Agregar una **IUnknown** puntero a la clase de objeto e inicialícela en **NULL** en el constructor.  
  
-   Reemplazar `FinalConstruct` para crear el agregado.  
  
-   Utilice la **IUnknown** puntero definido como parámetro para el [COM_INTERFACE_ENTRY_AGGREGATE](http://msdn.microsoft.com/library/c671fa40-a57b-4797-ae88-c9762dabd4dc) macro.  
  
-   Invalidar `FinalRelease` para liberar el **IUnknown** puntero.  
  
##  <a name="a-namefinalreleasea--ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a>CComObjectRootEx::FinalRelease  
 Puede invalidar este método en una clase derivada para realizar cualquier limpieza necesaria para el objeto.  
  
```
void FinalRelease();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `CComObjectRootEx::FinalRelease` no hace nada.  
  
 Realizar la limpieza en `FinalRelease` es preferible a agregar código al destructor de la clase, ya que el objeto se haya construido totalmente todavía en el momento en que `FinalRelease` se llama. Esto le permite tener acceso a los métodos proporcionados por la clase más derivada. Esto es especialmente importante para la liberación de los objetos agregados antes de la eliminación.  
  
##  <a name="a-nameinternaladdrefa--ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a>CComObjectRootEx::InternalAddRef  
 El recuento de referencias de un objeto no agregado se incrementa en 1.  
  
```
ULONG InternalAddRef();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para los diagnósticos y pruebas.  
  
### <a name="remarks"></a>Comentarios  
 Si el modelo de subprocesos es multiproceso, **InterlockedIncrement** se utiliza para impedir que varios subprocesos cambien el recuento de referencias al mismo tiempo.  
  
##  <a name="a-nameinternalqueryinterfacea--ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a>CComObjectRootEx:: InternalQueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `pThis`  
 [in] Un puntero al objeto que contiene el mapa COM de las interfaces expuestas a `QueryInterface`.  
  
 `pEntries`  
 [in] Un puntero a la **_ATL_INTMAP_ENTRY** estructura que tiene acceso a un mapa de las interfaces disponibles.  
  
 `iid`  
 [in] El GUID de la interfaz solicitada.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz especificado en `iid`, o **NULL** si no se encuentra la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
### <a name="remarks"></a>Comentarios  
 `InternalQueryInterface` solo administra interfaces de la tabla de asignación COM. Si se agrega el objeto, `InternalQueryInterface` no delegar en el desconocido externo. Puede especificar interfaces en el mapa COM con la macro [COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00) o uno de sus variantes.  
  
##  <a name="a-nameinternalreleasea--ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a>CComObjectRootEx::InternalRelease  
 Disminuye el contador de referencias de un objeto no agregado por 1.  
  
```
ULONG InternalRelease();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En ambos no son de depuración y versiones de depuración, esta función devuelve un valor que puede ser útil para el diagnóstico o de pruebas. El valor exacto devuelto depende de muchos factores, como el sistema operativo y puede o no, es el recuento de referencia.  
  
### <a name="remarks"></a>Comentarios  
 Si el modelo de subprocesos es multiproceso, **InterlockedDecrement** se utiliza para impedir que varios subprocesos cambien el recuento de referencias al mismo tiempo.  
  
##  <a name="a-namelocka--ccomobjectrootexlock"></a><a name="lock"></a>CComObjectRootEx::Lock  
 Si el modelo de subprocesos es multiproceso, este método llama a la función API de Win32 [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), que espera hasta que el subproceso puede tomar posesión del objeto de sección crítica obtenido a través de un miembro de datos privado.  
  
```
void Lock();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el código protegido termina de ejecutarse, el subproceso debe llamar a `Unlock` para liberar la propiedad de la sección crítica.  
  
 Si el modelo de subprocesos es de subproceso único, este método no hace nada.  
  
##  <a name="a-namemdwrefa--ccomobjectrootexmdwref"></a><a name="m_dwref"></a>CComObjectRootEx::m_dwRef  
 Parte de una unión que tiene acceso a cuatro bytes de memoria.  
  
```
long m_dwRef;
```  
  
### <a name="remarks"></a>Comentarios  
 Con `m_pOuterUnknown`, que forma parte de una unión:  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 Si no se agrega el objeto, el recuento de referencias accediendo `AddRef` y **versión** se almacena en `m_dwRef`. Si se agrega el objeto, el puntero para el desconocido externo se almacena en [m_pOuterUnknown](#m_pouterunknown).  
  
##  <a name="a-namempouterunknowna--ccomobjectrootexmpouterunknown"></a><a name="m_pouterunknown"></a>CComObjectRootEx::m_pOuterUnknown  
 Parte de una unión que tiene acceso a cuatro bytes de memoria.  
  
```
IUnknown*
    m_pOuterUnknown;
```     
  
### <a name="remarks"></a>Comentarios  
 Con `m_dwRef`, que forma parte de una unión:  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 Si se agrega el objeto, el puntero para el desconocido externo se almacena en `m_pOuterUnknown`. Si no se agrega el objeto, el recuento de referencias accediendo `AddRef` y **versión** se almacena en [m_dwRef](#m_dwref).  
  
##  <a name="a-nameobjectmaina--ccomobjectrootexobjectmain"></a><a name="objectmain"></a>CComObjectRootEx::ObjectMain  
 Para cada clase que se muestra en el [mapa de objetos](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f), esta función se llama una vez cuando se inicializa el módulo, y de nuevo cuando se finaliza.  
  
```
static void WINAPI ObjectMain(bool bStarting);
```  
  
### <a name="parameters"></a>Parámetros  
 `bStarting`  
 [out] El valor es **true** si la clase se inicializa; de lo contrario **false**.  
  
### <a name="remarks"></a>Comentarios  
 El valor de la `bStarting` parámetro indica si el módulo se va a inicializar o ha finalizado. La implementación predeterminada de `ObjectMain` no hace nada, pero puede invalidar esta función en su clase para inicializar o limpiar los recursos que desea asignar para la clase. Tenga en cuenta que `ObjectMain` se llama antes de que se solicitan todas las instancias de la clase.  
  
 `ObjectMain`se llama desde el punto de entrada de la DLL, por lo que el tipo de operación que puede realizar la función de punto de entrada está restringido. Para obtener más información sobre estas restricciones, consulte [comportamiento de la biblioteca de tiempo de ejecución](../../build/run-time-library-behavior.md) y [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM Nº&41;](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]  
  
##  <a name="a-nameouteraddrefa--ccomobjectrootexouteraddref"></a><a name="outeraddref"></a>CComObjectRootEx::OuterAddRef  
 Incrementa el recuento de referencias del objeto desconocido externo de una agregación.  
  
```
ULONG OuterAddRef();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para los diagnósticos y pruebas.  
  
##  <a name="a-nameouterqueryinterfacea--ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a>CComObjectRootEx::OuterQueryInterface  
 Recupera un puntero indirecto a la interfaz solicitada.  
  
```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz solicitada.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz especificado en `iid`, o **NULL** si la agregación no es compatible con la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
##  <a name="a-nameouterreleasea--ccomobjectrootexouterrelease"></a><a name="outerrelease"></a>CComObjectRootEx::OuterRelease  
 Disminuye el recuento de referencias del objeto desconocido externo de una agregación.  
  
```
ULONG OuterRelease();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En versiones no depuradas, siempre devuelve 0. En compilaciones de depuración, devuelve un valor que puede ser útil para el diagnóstico o de pruebas.  
  
##  <a name="a-nameunlocka--ccomobjectrootexunlock"></a><a name="unlock"></a>CComObjectRootEx::Unlock  
 Si el modelo de subprocesos es multiproceso, este método llama a la función API de Win32 [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), qué versiones de la propiedad del objeto de sección crítica obtenido a través de un miembro de datos privado.  
  
```
void Unlock();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener la propiedad, el subproceso debe llamar a `Lock`. Cada llamada a `Lock` requiere una llamada correspondiente a `Unlock` para liberar la propiedad de la sección crítica.  
  
 Si el modelo de subprocesos es de subproceso único, este método no hace nada.  
  
## <a name="see-also"></a>Vea también  
 [CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)   
 [CComObject (clase)](../../atl/reference/ccomobject-class.md)   
 [Clase CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

