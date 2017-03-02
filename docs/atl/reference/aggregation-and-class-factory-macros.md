---
title: "Agregación y Macros de clase de fábrica | Documentos de Microsoft"
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
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
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
ms.openlocfilehash: 4509f7be36e45cf96a938e30ec0f82ec0c9836b5
ms.lasthandoff: 02/24/2017

---
# <a name="aggregation-and-class-factory-macros"></a>Agregación y Macros de fábrica de clase
Estas macros proporcionan maneras de controlar la agregación y de la declaración de generadores de clases.  
  
|||  
|-|-|  
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Declara que el objeto puede ser agregados (predeterminado).|  
|[DECLARE_CLASSFACTORY](#declare_classfactory)|El generador de clases que se declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), el generador de clases ATL predeterminado.|  
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Declara el objeto de generador de clases para la clase de fábrica.|  
|[MACRO DECLARE_CLASSFACTORY2](#declare_classfactory2)|Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) a la clase de fábrica.|  
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) a la clase de fábrica.|  
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) a la clase de fábrica.|  
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Declara un virtual `GetControllingUnknown` (función).|  
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Declara que no se puede agregar el objeto.|  
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Declara que debe agregarse el objeto.|  
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Comprueba el valor del objeto desconocido externo y declara que su objeto agregable o no agregables, según corresponda.|  
|[MACRO DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Protege el objeto externo de eliminación durante la construcción de un objeto interno.|  
|[DECLARE_VIEW_STATUS](#declare_view_status)|Especifica la **VIEWSTATUS** marcas para el contenedor.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="a-namedeclareaggregatablea--declareaggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE  
 Especifica que puede agregarse el objeto.  
  
```
DECLARE_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre de la clase que se define como agregables.  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene esta macro para especificar el modelo de agregación predeterminado. Para invalidar este valor predeterminado, especifique el [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) o [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) macro en la definición de clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#121;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="a-namedeclareclassfactorya--declareclassfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY  
 Declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a la clase de fábrica.  
  
```
DECLARE_CLASSFACTORY()
```  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) utiliza esta macro para declarar el generador de clases predeterminado para el objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&#55;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]  
  
##  <a name="a-nameccomclassfactoryclassa--ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>CComClassFactory (clase)  
 Esta clase implementa la [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfaz.  
  
```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Comentarios  
 `CComClassFactory`implementa el [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfaz, que contiene métodos para crear un objeto de CLSID determinado, así como el generador de clases en la memoria para permitir que los nuevos objetos que se crean más rápidamente el bloqueo. **IClassFactory** deben implementarse para cada clase que se registra en el registro del sistema y de que asigna un CLSID.  
  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Para reemplazar este valor predeterminado, especifique uno de los `DECLARE_CLASSFACTORY` *XXX* macros en la definición de clase. Por ejemplo, el [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) macro utiliza la clase especificada para el generador de clases:  
  
 [!code-cpp[NVC_ATL_COM Nº&8;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
 La definición de clase anterior especifica que **CMyClassFactory** se utiliza como generador de clases predeterminado del objeto. **CMyClassFactory** debe derivar de `CComClassFactory` e invalidar `CreateInstance`.  
  
 ATL proporciona tres otras macros que declaran un generador de clases:  
  
- [Macro DECLARE_CLASSFACTORY2](#declare_classfactory2) utiliza [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación de una licencia.  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) utiliza [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios contenedores.  
  
- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) utiliza [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye una sola [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto.  
  
##  <a name="a-namedeclareclassfactoryexa--declareclassfactoryex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX  
 Declara `cf` a la clase de fábrica.  
  
```
DECLARE_CLASSFACTORY_EX( cf )
```  
  
### <a name="parameters"></a>Parámetros  
 `cf`  
 [in] El nombre de la clase que implementa el objeto de generador de clases.  
  
### <a name="remarks"></a>Comentarios  
 El `cf` parámetro debe derivarse de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) e invalidar el `CreateInstance` método.  
  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) (macro), que especifica `CComClassFactory` como el generador de clases de forma predeterminada. Sin embargo, mediante la inclusión de la `DECLARE_CLASSFACTORY_EX` (macro) en la definición de clase del objeto, invalida este valor predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM Nº&8;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
##  <a name="a-namedeclareclassfactory2a--declareclassfactory2"></a><a name="declare_classfactory2"></a>MACRO DECLARE_CLASSFACTORY2  
 Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) a la clase de fábrica.  
  
```
DECLARE_CLASSFACTORY2( lic )
```  
  
### <a name="parameters"></a>Parámetros  
 *LIC*  
 [in] Una clase que implementa `VerifyLicenseKey`, `GetLicenseKey`, y `IsLicenseValid`.  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) (macro), que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Sin embargo, mediante la inclusión de la `DECLARE_CLASSFACTORY2` (macro) en la definición de clase del objeto, invalida este valor predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&#2;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
##  <a name="a-nameccomclassfactory2classa--ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>Clase CComClassFactory2  
 Esta clase implementa la [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfaz.  
  
```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```    
  
### <a name="parameters"></a>Parámetros  
 *licencia*  
 Una clase que implementa las siguientes funciones estáticas:  
  
- **estático VerifyLicenseKey BOOL (BSTR** `bstr` **);**  
  
- **estático GetLicenseKey BOOL (DWORD** `dwReserved` **, BSTR\* ** `pBstr` **);**  
  
- **static BOOL IsLicenseValid ();**  
  
### <a name="remarks"></a>Comentarios  
 `CComClassFactory2`implementa el [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfaz, que es una extensión de [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364). **IClassFactory2** controles objeto creación a través de una licencia. Una fábrica de clase ejecutada en un equipo con licencia puede proporcionar una clave de licencia de tiempo de ejecución. Esta clave de licencia permite que una aplicación crear instancias de objetos cuando no existe una licencia completo de equipo.  
  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Usar `CComClassFactory2`, especifique el [macro DECLARE_CLASSFACTORY2](#declare_classfactory2) macro en la definición de clase del objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM&#2;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
 **CMyLicense**, el parámetro de plantilla a `CComClassFactory2`, debe implementar las funciones estáticas `VerifyLicenseKey`, `GetLicenseKey`, y `IsLicenseValid`. El siguiente es un ejemplo de una clase simple de licencia:  
  
 [!code-cpp[NVC_ATL_COM&3;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]  
  
 `CComClassFactory2`deriva de **CComClassFactory2Base** y *licencia*. **CComClassFactory2Base**, a su vez, deriva de **IClassFactory2** y **CComObjectRootEx\< CComGlobalsThreadModel >**.  
  
##  <a name="a-namedeclareclassfactoryautothreada--declareclassfactoryautothread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD  
 Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) a la clase de fábrica.  
  
```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) (macro), que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Sin embargo, mediante la inclusión de la `DECLARE_CLASSFACTORY_AUTO_THREAD` (macro) en la definición de clase del objeto, invalida este valor predeterminado.  
  
 Cuando se crean objetos en varios contenedores (en un servidor fuera de proceso), agregue `DECLARE_CLASSFACTORY_AUTO_THREAD` a la clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&#9;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="a-nameccomclassfactoryautothreadclassa--ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>Clase CComClassFactoryAutoThread  
 Esta clase implementa la [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfaz y permite que los objetos que se creen en varios contenedores.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Comentarios  
 `CComClassFactoryAutoThread`es similar a [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), pero permite que los objetos que se creen en varios contenedores. Para sacar partido de esta compatibilidad, derive su módulo EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Usar `CComClassFactoryAutoThread`, especifique el [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) macro en la definición de clase del objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM&#9;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="a-namedeclareclassfactorysingletona--declareclassfactorysingleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON  
 Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) a la clase de fábrica.  
  
```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```  
  
### <a name="parameters"></a>Parámetros  
 `obj`  
 [in] El nombre de su objeto de clase.  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) (macro), que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Sin embargo, mediante la inclusión de la `DECLARE_CLASSFACTORY_SINGLETON` (macro) en la definición de clase del objeto, invalida este valor predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&#10;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="a-nameccomclassfactorysingletonclassa--ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>Clase CComClassFactorySingleton  
 Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 La clase.  
  
 `CComClassFactorySingleton`se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único. Cada llamada a la `CreateInstance` método simplemente consulta este objeto de un puntero de interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Usar `CComClassFactorySingleton`, especifique el [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) macro en la definición de clase del objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM&#10;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="a-namedeclaregetcontrollingunknowna--declaregetcontrollingunknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN  
 Declara una función virtual `GetControllingUnknown`.  
  
```
DECLARE_GET_CONTROLLING_UNKNOWN()
```  
  
### <a name="remarks"></a>Comentarios  
 Agregue esta macro a su objeto, si recibe el mensaje de error del compilador `GetControllingUnknown` no está definido (por ejemplo, en **CComAggregateCreator**).  
  
##  <a name="a-namedeclarenotaggregatablea--declarenotaggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE  
 Especifica que no se puede agregar el objeto.  
  
```
DECLARE_NOT_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre del objeto de clase se define como no agregable.  
  
### <a name="remarks"></a>Comentarios  
 `DECLARE_NOT_AGGREGATABLE`hace `CreateInstance` para devolver un error ( **CLASS_E_NOAGGREGATION**) si se realiza un intento para agregar a su objeto.  
  
 De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene el [DECLARE_AGGREGATABLE](#declare_aggregatable) macro, que especifica que se puede agregar el objeto. Para invalidar este comportamiento predeterminado, incluya `DECLARE_NOT_AGGREGATABLE` en la definición de clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#121;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="a-namedeclareonlyaggregatablea--declareonlyaggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE  
 Especifica que debe agregarse el objeto.  
  
```
DECLARE_ONLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre del objeto de clase que se está definiendo como sólo agregables.  
  
### <a name="remarks"></a>Comentarios  
 `DECLARE_ONLY_AGGREGATABLE`se produce un error ( **E_FAIL**) si se realiza un intento para **CoCreate** el objeto como objeto no agregado.  
  
 De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene el [DECLARE_AGGREGATABLE](#declare_aggregatable) macro, que especifica que se puede agregar el objeto. Para invalidar este comportamiento predeterminado, incluya `DECLARE_ONLY_AGGREGATABLE` en la definición de clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#125;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]  
  
##  <a name="a-namedeclarepolyaggregatablea--declarepolyaggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE  
 Especifica que una instancia de **CComPolyObject \< ** *x* ** > ** se crea cuando se crea el objeto.  
  
```
DECLARE_POLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre del objeto de clase que se está definiendo como agregable o no agregables.  
  
### <a name="remarks"></a>Comentarios  
 Durante la creación, se comprueba el valor del objeto desconocido externo. Si es **NULL**, **IUnknown** se implementa para un objeto no agregado. Si el desconocido externo no es **NULL**, **IUnknown** se implementa para un objeto agregado.  
  
 La ventaja de usar `DECLARE_POLY_AGGREGATABLE` es evitar tener ambos `CComAggObject` y `CComObject` en su módulo para controlar los casos agregados y no agregados. Una sola `CComPolyObject` objeto controla ambos casos. Esto significa que existen una única copia de la tabla vtable y una copia de las funciones en el módulo. Si su tabla vtable es grande, puede reducir sustancialmente el tamaño del módulo. Sin embargo, si su tabla vtable es pequeña, usando `CComPolyObject` puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, como son `CComAggObject` y `CComObject`.  
  
 El `DECLARE_POLY_AGGREGATABLE` macro se declara automáticamente en el objeto si usa el Asistente para controles ATL para crear un control total.  
  
##  <a name="a-namedeclareprotectfinalconstructa--declareprotectfinalconstruct"></a><a name="declare_protect_final_construct"></a>MACRO DECLARE_PROTECT_FINAL_CONSTRUCT  

 Evita que se elimine si el objeto (durante [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) el objeto agregado interno incrementa el recuento de referencias, a continuación, disminuye el recuento en 0.  
  
```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```  
  
##  <a name="a-namedeclareviewstatusa--declareviewstatus"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS  
 Coloque esta macro en la clase de control de un control ActiveX ATL para especificar el **VIEWSTATUS** marcas para el contenedor.  
  
```
DECLARE_VIEW_STATUS( statusFlags )
```  
  
### <a name="parameters"></a>Parámetros  
 `statusFlags`  
 [in] El **VIEWSTATUS** marcas. Consulte [VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201) para obtener una lista de marcas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#126;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)

