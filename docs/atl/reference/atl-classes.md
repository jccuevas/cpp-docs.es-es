---
title: Clases y Structs ATL | Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 2bf13700ada3284b8a32718d21971e89e30e5b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498048"
---
# <a name="atl-classes-and-structs"></a>Clases y structs ATL

El Active Template Library (ATL) incluye las siguientes clases y Structs. Para buscar una clase determinada por categoría, vea la [información general de la clase ATL](../../atl/atl-class-overview.md).

|Class/struct|DESCRIPCIÓN|Archivo de encabezado|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|Contiene información que se usa para representar varios destinos, como una impresora, un metarchivo o un control ActiveX.|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|Contiene datos de instancia de clase en el código de ventana en ATL.|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|Lo utiliza cualquier proyecto que use ATL.|atlbase.h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|Lo usa el código relacionado con COM en ATL.| atlbase.h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|Contiene información de tipos que se usa para describir un método o una propiedad en una interfaz dispinterface.|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|Contiene los datos utilizados por cada módulo ATL.|atlbase.h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|Lo utiliza el código de ventana en ATL.|atlbase.h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|Esta clase la usan las macros de conversión de cadenas CA2TEX y CT2AEX, y la definición de tipo CA2A.|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|Esta clase se usa en las macros de conversión de cadenas CA2CTEX y CT2CAEX, y en la definición de tipo CA2CA.|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|Esta clase la usan las macros de conversión de cadenas CA2TEX, CA2CTEX, CT2WEX y CT2CWEX, y la definición de tipo CA2W.|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|Esta clase es un contenedor para un token de acceso.|atlsecurity.h|
|[CAcl](../../atl/reference/cacl-class.md)|Esta clase es un contenedor para una estructura ACL (lista de control de acceso).|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|Esta plantilla se utiliza para ajustar las clases que vuelven a definir el operador address-of para devolver algo distinto de la dirección del objeto.|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|Esta clase implementa un objeto de matriz.|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|Esta clase implementa un servidor COM de modelo de apartamento y agrupado de subprocesos.|atlbase.h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|Esta clase proporciona métodos para implementar un servidor COM de modelo de apartamento y agrupado de subprocesos.|atlbase.h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|Se crea una instancia de esta clase en cada proyecto ATL.|atlcore.h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|Esta clase implementa un módulo de servidor COM.|atlbase.h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|Esta clase proporciona compatibilidad con las interfaces de depuración.|atlbase.h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|Esta clase representa el módulo para un archivo DLL.|atlbase.h|
|[CAtlException](../../atl/reference/catlexception-class.md)|Esta clase define una excepción ATL.|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|Esta clase representa el módulo para una aplicación.|atlbase.h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|Esta clase proporciona un contenedor fino en torno a la API de control de archivos de Windows.|atlfile.h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|Esta clase representa un archivo asignado a la memoria, agregando un operador de conversión a los métodos de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).|atlfile.h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|Esta clase representa un archivo asignado a la memoria.|atlfile.h|
|[CAtlList](../../atl/reference/catllist-class.md)|Esta clase proporciona métodos para crear y administrar un objeto de lista.|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|Esta clase proporciona métodos para crear y administrar un objeto de mapa.|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|Esta clase proporciona métodos usados por varias clases de módulo ATL.|atlbase.h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|Esta clase implementa un módulo ATL.|atlbase.h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|Esta clase es una implementación ATL de una ventana que se coloca en una ventana host proporcionada por el shell para obtener una vista previa enriquecida.|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|Esta clase implementa un servicio.|atlbase.h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|Esta clase proporciona métodos para la creación y el uso de un archivo temporal.|atlfile.h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|Esta clase proporciona un contenedor para las funciones del administrador de transacciones de kernel (KTM).|atltransactionmanager.h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|Esta clase proporciona compatibilidad con los componentes de ventanas de ATL.|atlbase.h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|Esta clase representa un objeto de puntero inteligente.|atlbase.h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|Esta clase proporciona métodos útiles al construir una matriz de punteros inteligentes.|atlbase.h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|Esta clase proporciona métodos, funciones estáticas y definiciones de tipo útiles al crear colecciones de punteros inteligentes.|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|Esta clase proporciona métodos útiles al construir una lista de punteros inteligentes.|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|Esta clase representa un objeto de puntero inteligente mediante operadores New y Delete de vector.|atlbase.h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|Esta clase proporciona métodos, funciones estáticas y definiciones de tipos útiles al crear colecciones de punteros inteligentes mediante operadores New y Delete de vector.|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|Esta clase implementa un cuadro de diálogo (modal o no modal) que hospeda controles ActiveX.|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX.|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX y también admite el hospedaje de controles ActiveX con licencia.|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|Esta clase implementa la interfaz `IBindStatusCallback` .|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|Esta clase implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto agregado.|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|Esta clase proporciona métodos para administrar la memoria mediante rutinas de memoria COM.|atlbase.h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|Esta clase proporciona compatibilidad para administrar un contenedor en un módulo EXE agrupado por subprocesos.|atlbase.h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.|atlcore.h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|A partir de ATL 7,0 `CComAutoThreadModule` , está obsoleto: vea [módulos ATL](../../atl/atl-module-classes.md) para obtener más detalles.|atlbase.h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|Esta clase es un contenedor para BSTR.|atlbase.h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|Esta clase implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para una interfaz de recorte.|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|Esta clase implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|Esta clase implementa la interfaz [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|Esta clase implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) y permite crear objetos en varios apartamentos.|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un solo objeto.|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|Esta clase proporciona métodos para crear instancias de una clase y obtener sus propiedades.|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|Esta clase proporciona los métodos necesarios para implementar un control compuesto.|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|Esta clase implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) delegando en el del `IUnknown`objeto propietario.|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|Esta clase proporciona métodos para crear y administrar controles ATL.|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|Esta clase proporciona métodos para crear y administrar controles ATL.|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.|atlcore.h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|Esta clase proporciona métodos para bloquear y desbloquear un objeto de sección crítica.|atlbase.h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|Esta clase tiene métodos y operadores para crear y administrar un objeto CURRENCY.|atlcur.h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|Esta clase almacena una matriz de `IUnknown` punteros.|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|Esta clase define un objeto de enumerador COM basado en una matriz.|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|Esta clase proporciona la implementación de una interfaz de enumerador COM en la que los elementos que se van a enumerar se almacenan en una matriz.|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|Esta clase define un objeto de enumerador COM basado C++ en una colección de biblioteca estándar.|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|Esta clase proporciona los mismos métodos que [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) pero no proporciona una sección crítica.|atlcore.h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|Esta clase proporciona métodos para trabajar con punteros de interfaz y la tabla de interfaz global (GIT).|atlbase.h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) con las funciones de asignación de memoria de com.|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|Una clase de puntero inteligente para administrar los punteros del montón.|atlbase.h|
|[CComModule](../../atl/reference/ccommodule-class.md)|A partir de ATL 7,0 `CComModule` , está obsoleto: vea [módulos ATL](../../atl/atl-module-classes.md) para obtener más detalles.|atlbase.h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|Esta clase proporciona métodos seguros para subprocesos para aumentar y disminuir el valor de una variable.|atlbase.h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|Esta clase proporciona métodos seguros para subprocesos para aumentar y disminuir el valor de una variable, sin la funcionalidad crítica de bloqueo o desbloqueo de la sección.|atlbase.h|
|[CComObject](../../atl/reference/ccomobject-class.md)|Esta clase implementa `IUnknown` para un objeto no agregado.|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|Esta clase administra un recuento de referencias en el módulo `Base` que contiene el objeto.|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|Esta clase implementa `IUnknown` para un objeto no agregado, pero no incrementa el recuento de bloqueos del módulo en el constructor.|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Esta definición de tipo de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) se hace plantilla en el modelo de subprocesos predeterminado del servidor.|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|Esta clase proporciona métodos para controlar la administración del recuento de referencias de objetos para los objetos no agregados y los agregados.|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|Esta clase crea un objeto COM temporal y lo proporciona con una implementación esquemática de `IUnknown`.|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|Esta clase implementa `IUnknown` para un objeto agregado o no agregado.|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|Una clase de puntero inteligente para administrar punteros de interfaz COM.|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|Esta clase proporciona una base para las clases de puntero inteligente mediante rutinas de memoria basadas en COM.|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|Una clase de puntero inteligente para administrar punteros de interfaz COM.|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|Esta clase proporciona métodos, funciones estáticas y definiciones de tipo útiles al crear colecciones de punteros de interfaz COM.|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|Esta clase es un contenedor para la `SAFEARRAY Data Type` estructura.|atlsafe.h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|Esta clase es un contenedor para una `SAFEARRAYBOUND` estructura.|atlsafe.h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|Esta clase administra la selección de subprocesos para la clase [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).|atlbase.h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|Esta clase proporciona métodos para aumentar y disminuir el valor de una variable.|atlbase.h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|Esta clase implementa una interfaz de recorte.|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|Esta clase almacena `IUnknown` los punteros y está diseñado para usarse como un parámetro para la clase de plantilla [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|Esta clase ajusta el tipo de variante, proporcionando un miembro que indica el tipo de datos almacenados.|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|Esta clase implementa una ventana contenida dentro de otro objeto.|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|Esta clase proporciona métodos para administrar la memoria mediante rutinas de memoria de CRT.|atlcore.h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) con las funciones del montón de CRT.|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|Esta clase es un contenedor para una estructura DACL (lista de control de acceso discrecional).|atlsecurity.h|
|[CDebugReportHook (clase)](../../atl/reference/cdebugreporthook-class.md)|Utilice esta clase para enviar informes de depuración a una canalización con nombre.|atlutil. h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|Esta clase proporciona dos funciones estáticas para convertir caracteres entre mayúsculas y minúsculas.|atlcoll.h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|Esta clase proporciona funciones de comparación de elementos predeterminadas.|atlcoll.h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|Esta clase proporciona métodos y funciones predeterminados para una clase de colección.|atlcoll.h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|Esta clase proporciona una función estática para calcular los valores hash.|atlcoll.h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|Esta clase proporciona métodos para crear un cuadro de diálogo modal o no modal.|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|Esta clase proporciona métodos que admiten el encadenamiento dinámico de mapas de mensajes.|atlwin.h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|Las clases de colección usan esta clase para proporcionar métodos y funciones para mover, copiar, comparar y realizar operaciones hash.|atlcoll.h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|Esta clase proporciona los métodos de copia y movimiento predeterminados para una clase de colección.|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|Esta clase proporciona métodos para notificar al receptor del contenedor con respecto a los cambios de propiedad del control.|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) con las funciones del montón global de Win32.|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|Esta clase proporciona métodos para crear y usar un objeto de identificador.|atlbase.h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|Una clase de puntero inteligente para administrar los punteros del montón.|atlcore.h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|Esta clase constituye la base de varias clases de puntero de montón inteligente.|atlcore.h|
|[CHeapPtrElementTraits (clase)](../../atl/reference/cheapptrelementtraits-class.md)|Esta clase proporciona métodos, funciones estáticas y definiciones de tipo útiles al crear colecciones de punteros de montón.|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|Esta clase proporciona métodos útiles al construir una lista de punteros de montón.|atlcoll.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Proporciona compatibilidad mejorada con mapas de bits, incluida la capacidad de cargar y guardar imágenes en formatos JPEG, GIF, BMP y Portable Network Graphics (PNG).|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|Esta clase proporciona métodos útiles al construir una matriz de punteros de interfaz COM.|atlcoll.h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|Esta clase proporciona métodos útiles al construir una lista de punteros de interfaz COM.|atlcoll.h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) con las funciones del montón local de Win32.|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|Esta clase permite que otro objeto obtenga acceso a los mapas de mensajes de un objeto.|atlwin.h|
|[CNonStatelessWorker (clase)](../../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes de un grupo de subprocesos y las pasa a un objeto de trabajo que se crea y se destruye en cada solicitud.|atlutil. h|
|[CNoWorkerThread (clase)](../../atl/reference/cnoworkerthread-class.md)|Use esta clase como argumento para las clases `MonitorClass` de caché de parámetros de plantilla si desea deshabilitar el mantenimiento de la caché dinámica.|atlutil. h|
|[CPathT (clase)](../../atl/reference/cpatht-class.md)|Esta clase representa una ruta de acceso.|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|Esta clase proporciona métodos y funciones predeterminados para una clase de colección compuesta de tipos de datos primitivos.|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|Esta clase representa un objeto de descriptor de seguridad de objeto privado.|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|Esta clase representa una estructura de asignación, utilizando un árbol binario rojo-negro.|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|Esta clase representa una estructura de asignación que permite asociar cada clave a más de un valor, mediante un árbol binario rojo-negro.|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|Esta clase proporciona métodos para crear y usar un árbol rojo-negro.|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|Esta clase proporciona métodos para manipular entradas en el registro del sistema.|atlbase.h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|Esta clase proporciona la función de creación para un subproceso de CRT. Utilice esta clase si el subproceso va a utilizar funciones de CRT.|atlbase.h|
|[CSacl](../../atl/reference/csacl-class.md)|Esta clase es un contenedor para una estructura SACL (lista de control de acceso del sistema).|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|Esta clase es un contenedor fino de la `SECURITY_ATTRIBUTES` estructura.|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|Esta clase es un contenedor para la `SECURITY_DESCRIPTOR` estructura.|atlsecurity.h|
|[CSid](../../atl/reference/csid-class.md)|Esta clase es un contenedor para una `SID` estructura (identificador de seguridad).|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|Esta clase proporciona métodos para administrar una matriz simple.|atlsimpcoll. h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|Esta clase es una aplicación auxiliar para la clase [CSimpleArray](../../atl/reference/csimplearray-class.md) .|atlsimpcoll. h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|Esta clase es una aplicación auxiliar para la clase [CSimpleArray](../../atl/reference/csimplearray-class.md) .|atlsimpcoll. h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|Esta clase implementa un cuadro de diálogo modal básico.|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|Esta clase proporciona compatibilidad con una matriz de asignación simple.|atlsimpcoll. h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|Esta clase es una aplicación auxiliar para la clase [CSimpleMap](../../atl/reference/csimplemap-class.md) .|atlsimpcoll. h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|Esta clase es una aplicación auxiliar para la clase [CSimpleMap](../../atl/reference/csimplemap-class.md) .|atlsimpcoll. h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|Esta clase proporciona métodos para implementar un objeto de nodo de complemento.|atlsnap.h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|Esta clase proporciona métodos para implementar un objeto de página de propiedades de complemento.|atlsnap.h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|Esta clase proporciona métodos para admitir valores de propiedades estándar.|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|Esta clase proporciona funciones estáticas usadas por las clases `CString` de colección que almacenan objetos.|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|Esta clase proporciona funciones estáticas relacionadas con las cadenas almacenadas en objetos de clase de colección. Es similar a [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), pero realiza comparaciones que no distinguen mayúsculas de minúsculas.|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|Esta clase proporciona funciones estáticas relacionadas con las cadenas almacenadas en objetos de clase de colección. Los objetos de cadena se tratan como referencias.|atlcoll.h|
|[CThreadPool (clase)](../../atl/reference/cthreadpool-class.md)|Esta clase proporciona un grupo de subprocesos de trabajo que procesan una cola de elementos de trabajo.|atlutil. h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|Esta clase es un contenedor para la `TOKEN_GROUPS` estructura.|atlsecurity.h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|Esta clase es un contenedor para la `TOKEN_PRIVILEGES` estructura.|atlsecurity.h|
|[CUrl (clase)](../../atl/reference/curl-class.md)|Esta clase representa una dirección URL. Permite manipular cada elemento de la dirección URL independientemente de si se analiza una cadena de dirección URL existente o se crea una cadena desde cero.|atlutil. h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|Esta clase la usan las macros de conversión de cadenas CT2AEX, CW2TEX, CW2CTEX y CT2CAEX, y la definición de tipo CW2A.|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|Esta clase la usan las macros de conversión de cadenas CW2CTEX y CT2CWEX, y la definición de tipo CW2CW.|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|Esta clase la usan las macros de conversión de cadenas CW2TEX y CT2WEX, y la definición de tipo CW2W.|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) con las funciones de asignación del montón de Win32.|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|Esta clase proporciona métodos para manipular una ventana.|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|Esta clase proporciona métodos para crear o subclases de una ventana.|atlwin.h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|Esta clase proporciona un método para normalizar los estilos que se usan al crear un objeto de ventana.|atlwin.h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|Esta clase proporciona un método para normalizar los estilos que se usan al crear un objeto de ventana.|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|Esta clase proporciona métodos para registrar información para una clase de ventana.|atlwin.h|
|[CWorkerThread (clase)](../../atl/reference/cworkerthread-class.md)|Esta clase crea un subproceso de trabajo o utiliza uno existente, espera en uno o varios identificadores de objeto de kernel y ejecuta una función de cliente especificada cuando se señala uno de los identificadores.|atlutil. h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|Esta clase representa una interfaz para un `CreateInstance` método.|atlbase.h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|Esta clase representa la interfaz para un administrador de memoria.|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|Esta interfaz proporciona métodos para especificar características del contenedor o el control hospedado.|atlbase.h, ATLIFace.h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|Esta interfaz implementa propiedades de ambiente complementarias para un control hospedado.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|Esta interfaz proporciona métodos para manipular un control y su objeto host.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|Esta interfaz proporciona métodos para manipular un control con licencia y su objeto host.|atlbase.h, ATLIFace.h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|Esta clase proporciona métodos usados por una clase de colección.|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|Esta clase implementa un contenedor de puntos de conexión para administrar una colección de objetos [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|Esta clase implementa un punto de conexión.|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|Esta clase proporciona métodos para admitir Transferencia de datos uniformes y administrar conexiones.|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|Esta clase proporciona una implementación predeterminada para la `IDispatch` parte de una interfaz dual.|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|Esta clase proporciona implementaciones de los `IDispatch` métodos.|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|Esta clase proporciona implementaciones de los `IDispatch` métodos, sin obtener información de tipos de una biblioteca de tipos.|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Una interfaz al motor de análisis y representación HTML de Microsoft.|atlbase.h, ATLIFace.h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|Esta clase define una interfaz de enumerador basada C++ en una colección de biblioteca estándar.|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|Esta clase proporciona una implementación predeterminada de la `IObjectSafety` interfaz para permitir que un cliente recupere y establezca los niveles de seguridad de un objeto.|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|Esta clase proporciona métodos que permiten a un objeto comunicarse con su sitio.|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|Esta clase proporciona una implementación predeterminada de la `IOleControl` interfaz e `IUnknown`implementa.|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|Esta clase proporciona métodos para ayudar a la comunicación entre un control en contexto y su contenedor.|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|Esta clase implementa `IUnknown` y proporciona métodos que permiten a un control sin ventana recibir los mensajes de ventana y participar en las operaciones de arrastrar y colocar.|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|Esta clase implementa `IUnknown` y es la interfaz principal a través de la cual un contenedor se comunica con un control.|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|Esta clase implementa `IUnknown` y permite que un cliente tenga acceso a la información de las páginas de propiedades de un objeto.|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|Esta clase implementa `IUnknown` y permite a un objeto guardar sus propiedades en un contenedor de propiedades proporcionado por el cliente.|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|Esta clase implementa la interfaz [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) .|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la interfaz [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|Esta clase implementa `IUnknown` los métodos de la interfaz [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) .|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|Esta clase expone la interfaz [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) como una interfaz de salida en un objeto conectable.|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|Esta clase implementa `IUnknown` y hereda la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la interfaz [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) .|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|Esta clase proporciona una implementación predeterminada de los métodos [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) y [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) .|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|Esta clase combina la inicialización del control de los contenedores en una sola llamada.|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la interfaz [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) .|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|Esta clase proporciona una implementación predeterminada de la `IServiceProvider` interfaz.|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la interfaz [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) .|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|Esta clase proporciona una implementación predeterminada de la `ISupportErrorInfo Interface` interfaz y se puede usar cuando solo una sola interfaz genera errores en un objeto.|atlcom.h|
|[IThreadPoolConfig (interfaz)](../../atl/reference/ithreadpoolconfig-interface.md)|Esta interfaz proporciona métodos para configurar un grupo de subprocesos.|atlutil. h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|Esta `IUnknown` clase implementa y proporciona implementaciones predeterminadas de las interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)y [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) .|atlctl.h|
|[IWorkerThreadClient (interfaz)](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient`es la interfaz implementada por los clientes de la clase [CWorkerThread](../../atl/reference/cworkerthread-class.md) .|atlutil. h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|Esta clase proporciona contenedores para `CreateWindow` y. `CreateWindowEx`|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|Esta clase de adaptador de argumentos `RECT` permite pasar punteros o referencias a una función que se implementa en términos de punteros.|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|Esta clase de adaptador de argumentos permite pasar nombres de recursos (LPCTSTRs) o identificadores de recursos (UINT) a una función sin necesidad de que el autor de la llamada convierta el identificador en una cadena mediante la macro MAKEINTRESOURCE.|atlwin.h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|Esta clase proporciona la función de creación para un subproceso de Windows. Utilice esta clase si el subproceso no va a utilizar funciones de CRT.|atlbase.h|

## <a name="see-also"></a>Vea también

[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)<br/>
[Funciones](../../atl/reference/atl-functions.md)<br/>
[Variables globales](../../atl/reference/atl-global-variables.md)<br/>
[Typedefs](../../atl/reference/atl-typedefs.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
