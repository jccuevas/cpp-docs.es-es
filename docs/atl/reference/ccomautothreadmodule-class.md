---
title: La clase CComAutoThreadModule | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
caps.latest.revision: 21
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
ms.openlocfilehash: 07aaf6dc7029452fa6822c5f5f1ae09b724ddc8b
ms.lasthandoff: 02/24/2017

---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule (clase)
A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class ThreadAllocator = CComSimpleThreadAllocator>  
class CComAutoThreadModule : public CComModule
```  
  
#### <a name="parameters"></a>Parámetros  
 `ThreadAllocator`  
 [in] La clase de administración de selección de subproceso. El valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CreateInstance](#createinstance)|Selecciona un subproceso y, a continuación, crea un objeto en el contenedor asociado.|  
|[GetDefaultThreads](#getdefaultthreads)|(Estático) Calcula dinámicamente el número de subprocesos para el módulo en función del número de procesadores.|  
|[Init](#init)|Crea subprocesos del módulo.|  
|[Bloqueo](#lock)|Incrementa el recuento de bloqueos en el módulo y en el subproceso actual.|  
|[Desbloquear](#unlock)|Disminuye el recuento de bloqueos en el módulo y en el subproceso actual.|  
  
### <a name="data-members"></a>Miembros de datos  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[dwThreadID](#dwthreadid)|Contiene el identificador del subproceso actual.|  
|[m_Allocator](#m_allocator)|Administra la selección de subproceso.|  
|[m_nThreads](#m_nthreads)|Contiene el número de subprocesos en el módulo.|  
|[m_pApartments](#m_papartments)|Administra los apartamentos del módulo.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Esta clase está obsoleta, que ha reemplazado por la [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) y [CAtlModule](../../atl/reference/catlmodule-class.md) las clases derivadas. La siguiente información es para uso con versiones anteriores de ATL.  
  
 `CComAutoThreadModule`se deriva de [CComModule](../../atl/reference/ccommodule-class.md) para implementar un servidor COM de subprocesamiento de modelo, agrupadas por subproceso para servicios de Windows y los archivos exe. `CComAutoThreadModule`usa [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un contenedor para cada subproceso en el módulo.  
  
 Derivar su módulo de `CComAutoThreadModule` cuando desee crear objetos en varios contenedores. También debe incluir el [DECLARE_CLASSFACTORY_AUTO_THREAD](http://msdn.microsoft.com/library/19d7105e-03e8-4412-9f5e-5384c8a5e18f) macro en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases.  
  
 De forma predeterminada, el Asistente para aplicaciones de COM de ATL (el Asistente para proyectos ATL en Visual Studio. NET) se derivarán el módulo de `CComModule`. Usar `CComAutoThreadModule`, modifique la definición de clase. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_AxHost&#2;](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `IAtlAutoThreadModule`  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 [CComModule](../../atl/reference/ccommodule-class.md)  
  
 `CComAutoThreadModule`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="a-namecreateinstancea--ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a>CComAutoThreadModule::CreateInstance  
 A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```  
  
### <a name="parameters"></a>Parámetros  
 *pfnCreateInstance*  
 [in] Puntero a una función de creación.  
  
 `riid`  
 [in] El IID de la interfaz solicitada.  
  
 `ppvObj`  
 [out] Un puntero al puntero de interfaz identificado por `riid`. Si el objeto no admite esta interfaz, `ppvObj` se establece en NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Selecciona un subproceso y, a continuación, crea un objeto en el contenedor asociado.  
  
##  <a name="a-namedwthreadida--ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a>CComAutoThreadModule::dwThreadID  
 A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
DWORD dwThreadID;
```  
  
### <a name="remarks"></a>Comentarios  
 Contiene el identificador del subproceso actual.  
  
##  <a name="a-namegetdefaultthreadsa--ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads  
 A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de subprocesos que se creará en el módulo del archivo EXE.  
  
### <a name="remarks"></a>Comentarios  
 Esta función estática calcula dinámicamente el número máximo de subprocesos para el módulo EXE, en función del número de procesadores. De forma predeterminada, este valor devuelto se pasa a la [Init](#init) método para crear los subprocesos.  
  
##  <a name="a-nameinita--ccomautothreadmoduleinit"></a><a name="init"></a>CComAutoThreadModule::Init  
 A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Un puntero a una matriz de entradas de mapa de objeto.  
  
 `h`  
 [in] El `HINSTANCE` pasado a **DLLMain** o `WinMain`.  
  
 `plibid`  
 [in] Puntero a LIBID de la biblioteca de tipos asociado al proyecto.  
  
 `nThreads`  
 [in] El número de subprocesos que se va a crear. De forma predeterminada, `nThreads` es el valor devuelto por [GetDefaultThreads](#getdefaultthreads).  
  
### <a name="remarks"></a>Comentarios  
 Inicializa los miembros de datos y crea el número de subprocesos especificado por `nThreads`.  
  
##  <a name="a-namelocka--ccomautothreadmodulelock"></a><a name="lock"></a>CComAutoThreadModule::Lock  
 A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico o de pruebas.  
  
### <a name="remarks"></a>Comentarios  
 Realiza un incremento atómico en el recuento de bloqueos para el módulo y el subproceso actual. `CComAutoThreadModule`el recuento de bloqueos del módulo se utiliza para determinar si los clientes tienen acceso al módulo. El recuento de bloqueos en el subproceso actual se utiliza para fines estadísticos.  
  
##  <a name="a-namemallocatora--ccomautothreadmodulemallocator"></a><a name="m_allocator"></a>CComAutoThreadModule::m_Allocator  
 A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
ThreadAllocator  m_Allocator;
```     
  
### <a name="remarks"></a>Comentarios  
 El objeto de administración de selección de subproceso. De forma predeterminada, el `ThreadAllocator` parámetro de plantilla de clase es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
##  <a name="a-namemnthreadsa--ccomautothreadmodulemnthreads"></a><a name="m_nthreads"></a>CComAutoThreadModule::m_nThreads  
 A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
int m_nThreads;
```  
  
### <a name="remarks"></a>Comentarios  
 Contiene el número de subprocesos en el módulo del archivo EXE. Cuando [Init](#init) se llama, `m_nThreads` está establecido en el `nThreads` el valor del parámetro. Asociado de subprocesamiento cada estado administrado por un [CComApartment](../../atl/reference/ccomapartment-class.md) objeto.  
  
##  <a name="a-namempapartmentsa--ccomautothreadmodulempapartments"></a><a name="m_papartments"></a>CComAutoThreadModule::m_pApartments  
 A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
CComApartment* m_pApartments;
```  
  
### <a name="remarks"></a>Comentarios  
 Apunta a una matriz de [CComApartment](../../atl/reference/ccomapartment-class.md) objetos, cada uno de ellos administra un apartamento en el módulo. El número de elementos de la matriz se basa en el [m_nThreads](#m_nthreads) miembro.  
  
##  <a name="a-nameunlocka--ccomautothreadmoduleunlock"></a><a name="unlock"></a>CComAutoThreadModule::Unlock  
 A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico o de pruebas.  
  
### <a name="remarks"></a>Comentarios  
 Realiza un decremento atómica en el recuento de bloqueos para el módulo y el subproceso actual. `CComAutoThreadModule`el recuento de bloqueos del módulo se utiliza para determinar si los clientes tienen acceso al módulo. El recuento de bloqueos en el subproceso actual se utiliza para fines estadísticos.  
  
 Cuando el recuento de bloqueos del módulo llega a cero, se puede descargar el módulo.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)

