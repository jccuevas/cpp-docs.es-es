---
title: CComObjectRootEx (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
dev_langs:
- C++
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9ada8396f9d5473213f726acd27691a97a59847
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684798"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx (clase)
Esta clase proporciona métodos para controlar la administración de recuento de referencia de objeto para objetos agregados y agregados.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class ThreadModel>  
class CComObjectRootEx : public CComObjectRootBase
```  
  
#### <a name="parameters"></a>Parámetros  
 *ThreadModel*  
 La clase cuyos métodos implementan el modelo de subprocesos deseado. Puede elegir el modelo de subprocesos estableciendo explícitamente *ThreadModel* a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), o [ CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Puede aceptar el modelo de subprocesos predeterminado del servidor estableciendo *ThreadModel* a [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) o [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).  

  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CComObjectRootEx](#ccomobjectrootex)|Constructor.|  
|[InternalAddRef](#internaladdref)|Incrementa el recuento de referencias para un objeto no agregado.|  
|[InternalRelease](#internalrelease)|Disminuye el recuento de referencias para un objeto no agregado.|  
|[Bloqueo](#lock)|Si el modelo de subprocesos es multiproceso, obtiene la propiedad de un objeto de sección crítica.|  
|[Desbloquear](#unlock)|Si el modelo de subprocesos es multiproceso, libera la propiedad de un objeto de sección crítica.|  
  
### <a name="ccomobjectrootbase-methods"></a>Métodos CComObjectRootBase  
  
|||  
|-|-|  
|[FinalConstruct](#finalconstruct)|Reemplazar en la clase para realizar cualquier inicialización requerida por el objeto.|  
|[FinalRelease](#finalrelease)|Reemplazar en la clase para realizar las limpiezas requeridas por el objeto.|  
|[OuterAddRef](#outeraddref)|Incrementa el recuento de referencias para un objeto agregado.|  
|[OuterQueryInterface](#outerqueryinterface)|Delega en el exterior `IUnknown` de un objeto agregado.|  
|[OuterRelease](#outerrelease)|Disminuye el recuento de referencias para un objeto agregado.|  
  
### <a name="static-functions"></a>Funciones estáticas  
  
|||  
|-|-|  
|[InternalQueryInterface](#internalqueryinterface)|Delega en el `IUnknown` de un objeto no agregado.|  
|[ObjectMain](#objectmain)|Llamado durante la inicialización del módulo y finalización para las clases derivadas que se muestran en el mapa de objetos.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_dwRef](#m_dwref)|Con `m_pOuterUnknown`, que forma parte de una unión. Usar cuando no se agrega el objeto para contener el recuento de referencias de `AddRef` y `Release`.|  
|[m_pOuterUnknown](#m_pouterunknown)|Con `m_dwRef`, que forma parte de una unión. Se utiliza cuando se agrega el objeto para almacenar un puntero para el desconocido externo.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObjectRootEx` controla la administración de recuento de referencia de objeto para objetos agregados y agregados. Si no se agrega el objeto y mantiene el puntero para el desconocido externo si se agrega el objeto contiene el recuento de referencias de objeto. Para los objetos agregados, `CComObjectRootEx` métodos que pueden usarse para controlar el error del objeto interno para construir y se elimina proteger el objeto contra eliminación cuando se publican las interfaces internas externo o el objeto interno.  
  
 Una clase que implementa un servidor COM debe heredar de `CComObjectRootEx` o [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).  
  
 Si la definición de clase especifica la [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) macro, ATL crea una instancia de `CComPolyObject<CYourClass>` cuando `IClassFactory::CreateInstance` se llama. Durante la creación, se comprueba el valor del objeto desconocido externo. Si es NULL, `IUnknown` se implementa para un objeto no agregado. Si no es NULL, el desconocido externo `IUnknown` se implementa para un objeto agregado.  
  
 Si la clase no especifica la macro DECLARE_POLY_AGGREGATABLE, ATL crea una instancia de `CAggComObject<CYourClass>` para los objetos agregados o una instancia de `CComObject<CYourClass>` para objetos agregados.  
  
 La ventaja de usar `CComPolyObject` es que no tenga ambos `CComAggObject` y `CComObject` en el módulo para controlar los casos agregados y no agregados. Una sola `CComPolyObject` objeto administra ambos casos. Por lo tanto, solo una copia de la tabla vtable y una copia de las funciones existe en el módulo. Si su tabla vtable es grande, puede reducir sustancialmente el tamaño del módulo. Sin embargo, si su tabla vtable es pequeña, usando `CComPolyObject` puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, como son `CComAggObject` y `CComObject`.  
  
 Si el objeto es agregado, [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) se implementa mediante `CComAggObject` o `CComPolyObject`. Estas clases de delegación `QueryInterface`, `AddRef`, y `Release` las llamadas a `CComObjectRootEx`del `OuterQueryInterface`, `OuterAddRef`, y `OuterRelease` para reenviar al desconocido externo. Normalmente, invalida `CComObjectRootEx::FinalConstruct` en la clase para crear los objetos agregados e invalidar `CComObjectRootEx::FinalRelease` liberarlos objetos de agregado.  
  
 Si el objeto no es agregado, `IUnknown` se implementa mediante `CComObject` o `CComPolyObject`. En este caso, las llamadas a `QueryInterface`, `AddRef`, y `Release` se delegan a `CComObjectRootEx`del `InternalQueryInterface`, `InternalAddRef`, y `InternalRelease` para realizar las operaciones reales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx  
 El constructor inicializa el recuento de referencias en 0.  
  
```
CComObjectRootEx();
```  
  
##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct  
 Puede invalidar este método en una clase derivada para realizar cualquier inicialización necesaria para el objeto.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si funciona correctamente, o uno de los errores estándar de valores HRESULT.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `CComObjectRootEx::FinalConstruct` simplemente devuelve S_OK.  
  
 Existen ventajas al realizar la inicialización en `FinalConstruct` en lugar del constructor de la clase:  
  
-   No puede devolver un código de estado de un constructor, pero puede devolver un valor HRESULT por medio de `FinalConstruct`del valor devuelto. Cuando se crean los objetos de la clase utilizando el generador de clases estándar proporcionado por ATL, este valor devuelto se propaga al cliente COM que permite proporcionar información detallada del error.  
  
-   No se puede llamar a funciones virtuales a través del mecanismo de función virtual desde el constructor de una clase. Llamar a una función virtual desde el constructor de una clase da como resultado una llamada a la función resuelta estáticamente según se define en la jerarquía de herencia en ese momento. Las llamadas a funciones virtuales puras dar lugar a errores del vinculador.  
  
     La clase no es la clase más derivada en la jerarquía de herencia, se basa en una clase derivada proporcionada por ATL para proporcionar parte de su funcionalidad. Hay muchas posibilidades de que la inicialización se deberá usar las características proporcionadas por esa clase (Esto es especialmente cierto cuando los objetos de la clase necesitan agregar otros objetos), pero el constructor de la clase no tiene forma de obtener acceso a esas características. El código de construcción de la clase se ejecuta antes de la clase más derivada se construye totalmente.  
  
     Sin embargo, `FinalConstruct` se llama inmediatamente después de la más derivada clase se construye totalmente lo que le permite llamar a funciones virtuales y usar la implementación de recuento de referencias proporcionada por ATL.  
  
### <a name="example"></a>Ejemplo  
 Normalmente, invalide este método en la clase derivada de `CComObjectRootEx` cree agregadas en objetos. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]  
  
 Si se produce un error en la construcción, puede devolver un error. También puede usar la macro [macro DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) impedir que el objeto externo está eliminado si, durante la creación, el objeto agregado interno incrementa el recuento de referencias, a continuación, disminuye el recuento a 0.  
  
 Aquí es una forma habitual de crear una función de agregado:  
  
-   Agregar un `IUnknown` puntero a la clase de objeto y se inicializa en NULL en el constructor.  
  
-   Invalidar `FinalConstruct` para crear el agregado.  
  
-   Use la `IUnknown` define como el parámetro de puntero la [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) macro.  
  
-   Invalidar `FinalRelease` para liberar el `IUnknown` puntero.  
  
##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease  
 Puede invalidar este método en una clase derivada para realizar cualquier limpieza necesaria para el objeto.  
  
```
void FinalRelease();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `CComObjectRootEx::FinalRelease` no hace nada.  
  
 Limpiando en `FinalRelease` es preferible a agregar código al destructor de la clase, puesto que el objeto se construye totalmente todavía en el momento en que `FinalRelease` se llama. Esto le permite obtener acceso seguro a los métodos proporcionados por la clase más derivada. Esto es especialmente importante para liberar los objetos agregados antes de la eliminación.  
  
##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef  
 Incrementa el recuento de referencias de un objeto agregado en 1.  
  
```
ULONG InternalAddRef();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico y prueba.  
  
### <a name="remarks"></a>Comentarios  
 Si el modelo de subprocesos es multiproceso, `InterlockedIncrement` se usa para evitar que más de un subproceso cambie el recuento de referencias al mismo tiempo.  
  
##  <a name="internalqueryinterface"></a>  CComObjectRootEx:: InternalQueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 *pThis*  
 [in] Un puntero al objeto que contiene el mapa COM de las interfaces expuestas a `QueryInterface`.  
  
 *pEntries*  
 [in] Un puntero a la `_ATL_INTMAP_ENTRY` estructura que tiene acceso a un mapa de las interfaces disponibles.  
  
 *IID*  
 [in] El GUID de la interfaz que se solicita.  
  
 *ppvObject*  
 [out] Un puntero al puntero de interfaz especificado en *iid*, o NULL si no se encuentra la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 `InternalQueryInterface` solo administra interfaces de la tabla de asignación COM. Si el objeto es agregado, `InternalQueryInterface` no delegar en el desconocido externo. Puede especificar interfaces en el mapa COM con la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) o uno de sus variantes.  
  
##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease  
 Disminuye el recuento de referencias de un objeto agregado por 1.  
  
```
ULONG InternalRelease();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En ambos no sean de depuración y las compilaciones de depuración, esta función devuelve un valor que puede ser útil para el diagnóstico o de pruebas. Devuelve el valor exacto depende de muchos factores, como el sistema operativo usado y puede ser o no, ser el recuento de referencias.  
  
### <a name="remarks"></a>Comentarios  
 Si el modelo de subprocesos es multiproceso, `InterlockedDecrement` se usa para evitar que más de un subproceso cambie el recuento de referencias al mismo tiempo.  
  
##  <a name="lock"></a>  CComObjectRootEx::Lock  
 Si el modelo de subprocesos es multiproceso, este método llama a la función de la API Win32 [EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection), que espera hasta que el subproceso puede tomar posesión del objeto de sección crítica obtenido a través de un miembro de datos privado.  
  
```
void Lock();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando termine de ejecutarse el código protegido, el subproceso debe llamar a `Unlock` para liberar la propiedad de la sección crítica.  
  
 Si el modelo de subprocesos tiene un único subproceso, este método no hace nada.  
  
##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef  
 Parte de una unión que se accede a cuatro bytes de memoria.  
  
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
  
 Si el objeto no es agregado, el recuento de referencias accediendo `AddRef` y `Release` se almacena en `m_dwRef`. Si el objeto es agregado, se almacena el puntero al desconocido externo en [m_pOuterUnknown](#m_pouterunknown).  
  
##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown  
 Parte de una unión que se accede a cuatro bytes de memoria.  
  
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
  
 Si el objeto es agregado, el puntero para el desconocido externo se almacena en `m_pOuterUnknown`. Si el objeto no es agregado, el recuento de referencias accediendo `AddRef` y `Release` se almacena en [m_dwRef](#m_dwref).  
  
##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain  
 Para cada clase que aparece en el mapa de objetos, esta función se llama una vez cuando se inicializa el módulo, y otra vez cuando se termina.  
  
```
static void WINAPI ObjectMain(bool bStarting);
```  
  
### <a name="parameters"></a>Parámetros  
 *bStarting*  
 [out] El valor es TRUE si la clase se está inicializando; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 El valor de la *bStarting* parámetro indica si el módulo se va a inicializar o ha finalizado. La implementación predeterminada de `ObjectMain` no hace nada, pero puede invalidar esta función en la clase para inicializar o limpiar los recursos que desea asignar para la clase. Tenga en cuenta que `ObjectMain` se llama antes de que se solicitan todas las instancias de la clase.  
  
 `ObjectMain` se llama desde el punto de entrada del archivo DLL, por lo que el tipo de operación que puede realizar la función de punto de entrada está restringido. Para obtener más información sobre estas restricciones, vea [Visual C++ y archivos DLL de comportamiento de la biblioteca de tiempo de ejecución](../../build/run-time-library-behavior.md) y [DllMain](/windows/desktop/Dlls/dllmain).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]  
  
##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef  
 Incrementa el recuento de referencias del objeto desconocido externo de una agregación.  
  
```
ULONG OuterAddRef();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico y prueba.  
  
##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface  
 Recupera un puntero indirecto a la interfaz solicitada.  
  
```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 *IID*  
 [in] El GUID de la interfaz que se solicita.  
  
 *ppvObject*  
 [out] Un puntero al puntero de interfaz especificado en *iid*, o NULL si la agregación no es compatible con la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease  
 Disminuye el recuento de referencias del objeto desconocido externo de una agregación.  
  
```
ULONG OuterRelease();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En versiones no depuradas, siempre devuelve 0. En las compilaciones de depuración, devuelve un valor que puede ser útil para el diagnóstico o de pruebas.  
  
##  <a name="unlock"></a>  CComObjectRootEx::Unlock  
 Si el modelo de subprocesos es multiproceso, este método llama a la función de la API Win32 [LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection), que libera la propiedad del objeto de sección crítica obtenido a través de un miembro de datos privado.  
  
```
void Unlock();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener la propiedad, el subproceso debe llamar a `Lock`. Cada llamada a `Lock` requiere una llamada correspondiente a `Unlock` para liberar la propiedad de la sección crítica.  
  
 Si el modelo de subprocesos tiene un único subproceso, este método no hace nada.  
  
## <a name="see-also"></a>Vea también  
 [CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)   
 [CComObject (clase)](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject (clase)](../../atl/reference/ccompolyobject-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
