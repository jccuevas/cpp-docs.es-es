---
title: Agregación y Macros de clase de fábrica
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 889ed4bbfc21209a64cfd9e4fee4b2335ce62010
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274900"
---
# <a name="aggregation-and-class-factory-macros"></a>Agregación y Macros de clase de fábrica

Estas macros proporcionan formas de controlar la agregación y de la declaración de generadores de clases.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Declara que el objeto puede ser agregados (predeterminado).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|El generador de clases que se declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), el generador de clases ATL predeterminado.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Declara el objeto de generador de clases que el generador de clases.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) sea el generador de clases.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) sea el generador de clases.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) sea el generador de clases.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Declara un virtual `GetControllingUnknown` función.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Declara que no se puede agregar el objeto.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Declara que debe agregarse el objeto.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Comprueba el valor del objeto desconocido externo y declara el objeto agregable o no agregables, según corresponda.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|El objeto externo se protege contra la eliminación durante la construcción de un objeto interno.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Especifica las marcas VIEWSTATUS al contenedor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="declare_aggregatable"></a>  DECLARE_AGGREGATABLE

Especifica que se puede agregar el objeto.

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
[in] El nombre de la clase que está definiendo como agregables.

### <a name="remarks"></a>Comentarios

[CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene esta macro para especificar el modelo de agregación predeterminado. Para invalidar este comportamiento predeterminado, especifique el [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) o [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) macro en la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_classfactory"></a>  DECLARE_CLASSFACTORY

Declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) sea el generador de clases.

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Comentarios

[CComCoClass](../../atl/reference/ccomcoclass-class.md) utiliza esta macro para declarar el generador de clases predeterminado para el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

##  <a name="ccomclassfactory_class"></a>  CComClassFactory (clase)

Esta clase implementa la [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfaz.

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Comentarios

`CComClassFactory` implementa el [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfaz, que contiene métodos para crear un objeto de un CLSID determinado, así como el generador de clases en la memoria para permitir que los nuevos objetos se pueden crear más rápidamente el bloqueo. `IClassFactory` se debe implementar para todas las clases que se registran en el registro del sistema y que asigna un CLSID.

Objetos ATL adquieren normalmente un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Para invalidar este comportamiento predeterminado, especifique uno de los DECLARE_CLASSFACTORY*XXX* macros en la definición de clase. Por ejemplo, el [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) macro usa la clase especificada para el generador de clases:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

La definición de clase anterior especifica que `CMyClassFactory` se usará como el generador de clases predeterminado del objeto. `CMyClassFactory` debe derivar de `CComClassFactory` e invalidar `CreateInstance`.

ATL proporciona tres otras macros que declaran un generador de clases:

- [Macro DECLARE_CLASSFACTORY2](#declare_classfactory2) usa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación a través de una licencia.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) usa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios contenedores.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) usa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye una sola [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto.

##  <a name="declare_classfactory_ex"></a>  DECLARE_CLASSFACTORY_EX

Declara `cf` sea el generador de clases.

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parámetros

*cf*<br/>
[in] El nombre de la clase que implementa el objeto de generador de clases.

### <a name="remarks"></a>Comentarios

El *cf* parámetro debe derivar de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) e invalidar la `CreateInstance` método.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) macro, que especifica `CComClassFactory` como el generador de clases de forma predeterminada. Sin embargo, en la definición de clase del objeto, incluyendo la macro DECLARE_CLASSFACTORY_EX, invalidar este comportamiento predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

##  <a name="declare_classfactory2"></a>  DECLARE_CLASSFACTORY2

Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) sea el generador de clases.

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parámetros

*lic*<br/>
[in] Una clase que implementa `VerifyLicenseKey`, `GetLicenseKey`, y `IsLicenseValid`.

### <a name="remarks"></a>Comentarios

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) macro, que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Sin embargo, en la definición de clase del objeto, incluyendo la macro de macro DECLARE_CLASSFACTORY2, invalidar este comportamiento predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

##  <a name="ccomclassfactory2_class"></a>  CComClassFactory2 Class

Esta clase implementa la [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfaz.

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parámetros

*license*<br/>
Una clase que implementa las funciones estáticas siguientes:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Comentarios

`CComClassFactory2` implementa el [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfaz, que es una extensión de [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2` creación de objetos de los controles a través de una licencia. Una clase factory ejecutada en un equipo con licencia puede proporcionar una clave de licencia de tiempo de ejecución. Esta clave de licencia permite que una aplicación crear instancias de objetos cuando no existe una licencia de toda la máquina.

Objetos ATL adquieren normalmente un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Para usar `CComClassFactory2`, especifique el [macro DECLARE_CLASSFACTORY2](#declare_classfactory2) macro en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, el parámetro de plantilla `CComClassFactory2`, debe implementar las funciones estáticas `VerifyLicenseKey`, `GetLicenseKey`, y `IsLicenseValid`. El siguiente es un ejemplo de una clase simple de licencia:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2` se deriva de ambos `CComClassFactory2Base` y *licencia*. `CComClassFactory2Base`, a su vez, deriva `IClassFactory2` y **CComObjectRootEx\< CComGlobalsThreadModel >**.

##  <a name="declare_classfactory_auto_thread"></a>  DECLARE_CLASSFACTORY_AUTO_THREAD

Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) sea el generador de clases.

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Comentarios

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) macro, que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Sin embargo, en la definición de clase del objeto, incluyendo la macro DECLARE_CLASSFACTORY_AUTO_THREAD, invalidar este comportamiento predeterminado.

Cuando se crean objetos en varios contenedores (en un servidor fuera de proceso), agregue DECLARE_CLASSFACTORY_AUTO_THREAD a la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="ccomclassfactoryautothread_class"></a>  CComClassFactoryAutoThread Class

Esta clase implementa la [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfaz y permite que los objetos que se creará en varios contenedores.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Comentarios

`CComClassFactoryAutoThread` es similar a [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), pero permite que los objetos que se creará en varios contenedores. Para aprovechar las ventajas de esta compatibilidad, derivan del módulo EXE desde [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Objetos ATL adquieren normalmente un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Para usar `CComClassFactoryAutoThread`, especifique el [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) macro en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="declare_classfactory_singleton"></a>  DECLARE_CLASSFACTORY_SINGLETON

Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) sea el generador de clases.

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
[in] El nombre de su objeto de clase.

### <a name="remarks"></a>Comentarios

[CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) macro, que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Sin embargo, en la definición de clase del objeto, incluyendo la macro DECLARE_CLASSFACTORY_SINGLETON, invalidar este comportamiento predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="ccomclassfactorysingleton_class"></a>  CComClassFactorySingleton (clase)

Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase.

`CComClassFactorySingleton` se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único. Cada llamada a la `CreateInstance` método simplemente consulta este objeto para un puntero de interfaz.

### <a name="remarks"></a>Comentarios

Objetos ATL adquieren normalmente un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Para usar `CComClassFactorySingleton`, especifique el [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) macro en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="declare_get_controlling_unknown"></a>  DECLARE_GET_CONTROLLING_UNKNOWN

Declara una función virtual `GetControllingUnknown`.

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Comentarios

Agregue esta macro a su objeto, si recibe el mensaje de error del compilador `GetControllingUnknown` no está definido (por ejemplo, en `CComAggregateCreator`).

##  <a name="declare_not_aggregatable"></a>  DECLARE_NOT_AGGREGATABLE

Especifica que no se puede agregar el objeto.

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
[in] El nombre del objeto de clase se define como no agregable.

### <a name="remarks"></a>Comentarios

Hace que DECLARE_NOT_AGGREGATABLE `CreateInstance` para devolver un error (CLASS_E_NOAGGREGATION) si se ha intentado van a agregar a su objeto.

De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene el [DECLARE_AGGREGATABLE](#declare_aggregatable) macro, que especifica que se puede agregar el objeto. Para invalidar este comportamiento predeterminado, incluya DECLARE_NOT_AGGREGATABLE en la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_only_aggregatable"></a>  DECLARE_ONLY_AGGREGATABLE

Especifica que debe agregarse el objeto.

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
[in] El nombre del objeto de clase se definen como sólo agregables.

### <a name="remarks"></a>Comentarios

DECLARE_ONLY_AGGREGATABLE produce un error (E_FAIL) si se realiza un intento para `CoCreate` su objeto como objeto agregada.

De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene el [DECLARE_AGGREGATABLE](#declare_aggregatable) macro, que especifica que se puede agregar el objeto. Para invalidar este comportamiento predeterminado, incluya DECLARE_ONLY_AGGREGATABLE en la definición de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

##  <a name="declare_poly_aggregatable"></a>  DECLARE_POLY_AGGREGATABLE

Especifica que una instancia de **CComPolyObject \<**  *x* **>** se crea cuando se crea el objeto.

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
[in] El nombre del objeto de clase se define como no agregable o agregables.

### <a name="remarks"></a>Comentarios

Durante la creación, se comprueba el valor del objeto desconocido externo. Si es NULL, `IUnknown` se implementa para un objeto no agregado. Si no es NULL, el desconocido externo `IUnknown` se implementa para un objeto agregado.

La ventaja de usar DECLARE_POLY_AGGREGATABLE es que no tenga ambos `CComAggObject` y `CComObject` en el módulo para controlar los casos agregados y no agregados. Una sola `CComPolyObject` objeto administra ambos casos. Esto significa que existen solo una copia de la tabla vtable y una copia de las funciones del módulo. Si su tabla vtable es grande, puede reducir sustancialmente el tamaño del módulo. Sin embargo, si su tabla vtable es pequeña, usando `CComPolyObject` puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, como son `CComAggObject` y `CComObject`.

La macro DECLARE_POLY_AGGREGATABLE automáticamente se declara en el objeto si usa al Asistente para controles ATL para crear un control total.

##  <a name="declare_protect_final_construct"></a>  DECLARE_PROTECT_FINAL_CONSTRUCT

Protege el objeto que se eliminen si (durante [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) el objeto agregado interno incrementa el recuento de referencias, a continuación, disminuye el recuento a 0.

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

##  <a name="declare_view_status"></a>  DECLARE_VIEW_STATUS

Colocar esta macro en la clase de control de un control ActiveX de ATL para especificar las marcas VIEWSTATUS al contenedor.

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parámetros

*statusFlags*<br/>
[in] Las marcas VIEWSTATUS. Consulte [VIEWSTATUS](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) para obtener una lista de marcas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
