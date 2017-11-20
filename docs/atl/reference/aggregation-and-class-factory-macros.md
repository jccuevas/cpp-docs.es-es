---
title: "Macros de clase de generador y agregación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ce4021ee01052f1c830bba5ad1932898fd84b281
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="aggregation-and-class-factory-macros"></a>Agregación y Macros de fábrica de clase
Estas macros proporcionan diversas formas de controlar la agregación y de la declaración de los generadores de clases.  
  
|||  
|-|-|  
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Declara que el objeto puede ser agregado (el valor predeterminado).|  
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Declara el generador de clases como [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), el generador de clases ATL predeterminado.|  
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Declara el objeto de generador de clases como el generador de clases.|  
|[MACRO DECLARE_CLASSFACTORY2](#declare_classfactory2)|Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) como el generador de clases.|  
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases.|  
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) como el generador de clases.|  
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Declara un virtual `GetControllingUnknown` función.|  
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Declara que no se puede agregar el objeto.|  
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Declara que debe agregarse el objeto.|  
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Comprueba el valor del objeto desconocido externo y declare el objeto agregable o no es agregable, según corresponda.|  
|[MACRO DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|El objeto externo se protege contra eliminación durante la construcción de un objeto interno.|  
|[DECLARE_VIEW_STATUS](#declare_view_status)|Especifica la **VIEWSTATUS** marcas para el contenedor.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE  
 Especifica que se puede agregar el objeto.  
  
```
DECLARE_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre de la clase que se define como agregables.  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene esta macro para especificar el modelo de agregación predeterminado. Para invalidar este comportamiento predeterminado, especifique el [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) o [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) macro en la definición de clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_classfactory"></a>DECLARE_CLASSFACTORY  
 Declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases.  
  
```
DECLARE_CLASSFACTORY()
```  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) utiliza esta macro para declarar el generador de clases predeterminado para el objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]  
  
##  <a name="ccomclassfactory_class"></a>CComClassFactory (clase)  
 Esta clase implementa la [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfaz.  
  
```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Comentarios  
 `CComClassFactory`implementa el [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfaz, que contiene métodos para crear un objeto de CLSID determinado, así como el generador de clases en la memoria para permitir que los nuevos objetos que se crean más rápidamente el bloqueo. **IClassFactory** debe implementarse para todas las clases que se registran en el registro del sistema y a la que se asigna un CLSID.  
  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Para invalidar este comportamiento predeterminado, especifique uno de los `DECLARE_CLASSFACTORY` *XXX* macros en la definición de clase. Por ejemplo, el [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) macro utiliza la clase especificada para el generador de clases:  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
 La definición de clase anterior especifica que **CMyClassFactory** se usará como generador de clases predeterminado del objeto. **CMyClassFactory** debe derivarse de `CComClassFactory` e invalidar `CreateInstance`.  
  
 ATL proporciona tres otras macros que declaran un generador de clases:  
  
- [Macro DECLARE_CLASSFACTORY2](#declare_classfactory2) utiliza [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación a través de una licencia.  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) utiliza [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios contenedores.  
  
- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) utiliza [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye una sola [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto.  
  
##  <a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX  
 Declara `cf` como el generador de clases.  
  
```
DECLARE_CLASSFACTORY_EX( cf )
```  
  
### <a name="parameters"></a>Parámetros  
 `cf`  
 [in] El nombre de la clase que implementa el objeto de generador de clases.  
  
### <a name="remarks"></a>Comentarios  
 El `cf` parámetro debe derivarse de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) e invalide el `CreateInstance` método.  
  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) macro, que especifica `CComClassFactory` como el generador de clases de forma predeterminada. Sin embargo, mediante la inclusión de la `DECLARE_CLASSFACTORY_EX` macro en la definición de clase del objeto, invalidar este valor predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
##  <a name="declare_classfactory2"></a>MACRO DECLARE_CLASSFACTORY2  
 Declara [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) como el generador de clases.  
  
```
DECLARE_CLASSFACTORY2( lic )
```  
  
### <a name="parameters"></a>Parámetros  
 *LIC*  
 [in] Una clase que implementa `VerifyLicenseKey`, `GetLicenseKey`, y `IsLicenseValid`.  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) macro, que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Sin embargo, mediante la inclusión de la `DECLARE_CLASSFACTORY2` macro en la definición de clase del objeto, invalidar este valor predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
##  <a name="ccomclassfactory2_class"></a>Clase CComClassFactory2  
 Esta clase implementa la [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfaz.  
  
```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```    
  
### <a name="parameters"></a>Parámetros  
 *licencia*  
 Una clase que implementa las funciones estáticas siguientes:  
  
- **estática VerifyLicenseKey BOOL (BSTR** `bstr` **);**  
  
- **estática GetLicenseKey BOOL (DWORD** `dwReserved` **, BSTR\***  `pBstr` **);**  
  
- **static BOOL IsLicenseValid ();**  
  
### <a name="remarks"></a>Comentarios  
 `CComClassFactory2`implementa el [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfaz, que es una extensión de [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364). **IClassFactory2** controles objeto creación a través de una licencia. Una ejecución de fábrica de clase en un equipo con licencia puede proporcionar una clave de licencia de tiempo de ejecución. Esta clave de licencia permite que una aplicación crear instancias de objetos cuando no existe una licencia completo de equipo.  
  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Usar `CComClassFactory2`, especifique el [macro DECLARE_CLASSFACTORY2](#declare_classfactory2) macro en la definición de clase del objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
 **CMyLicense**, el parámetro de plantilla `CComClassFactory2`, debe implementar las funciones estáticas `VerifyLicenseKey`, `GetLicenseKey`, y `IsLicenseValid`. El siguiente es un ejemplo de una clase simple de licencia:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]  
  
 `CComClassFactory2`se deriva de ambos **CComClassFactory2Base** y *licencia*. **CComClassFactory2Base**, a su vez, deriva de **IClassFactory2** y **CComObjectRootEx\< CComGlobalsThreadModel >**.  
  
##  <a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD  
 Declara [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases.  
  
```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) macro, que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Sin embargo, mediante la inclusión de la `DECLARE_CLASSFACTORY_AUTO_THREAD` macro en la definición de clase del objeto, invalidar este valor predeterminado.  
  
 Cuando se crean objetos en varios contenedores (en un servidor fuera de proceso), agregue `DECLARE_CLASSFACTORY_AUTO_THREAD` a la clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="ccomclassfactoryautothread_class"></a>Clase CComClassFactoryAutoThread  
 Esta clase implementa la [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) de interfaz y permite a los objetos que se creen en varios contenedores.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Comentarios  
 `CComClassFactoryAutoThread`es similar a [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), pero permite que los objetos que se creen en varios contenedores. Para sacar partido de esta compatibilidad, derive su módulo EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Usar `CComClassFactoryAutoThread`, especifique el [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) macro en la definición de clase del objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON  
 Declara [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) como el generador de clases.  
  
```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```  
  
### <a name="parameters"></a>Parámetros  
 `obj`  
 [in] El nombre de su objeto de clase.  
  
### <a name="remarks"></a>Comentarios  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md) incluye la [DECLARE_CLASSFACTORY](#declare_classfactory) macro, que especifica [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases de forma predeterminada. Sin embargo, mediante la inclusión de la `DECLARE_CLASSFACTORY_SINGLETON` macro en la definición de clase del objeto, invalidar este valor predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="ccomclassfactorysingleton_class"></a>Clase CComClassFactorySingleton  
 Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 La clase.  
  
 `CComClassFactorySingleton`se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único. Cada llamada a la `CreateInstance` método simplemente consulta este objeto para un puntero de interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Usar `CComClassFactorySingleton`, especifique el [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) macro en la definición de clase del objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN  
 Declara una función virtual `GetControllingUnknown`.  
  
```
DECLARE_GET_CONTROLLING_UNKNOWN()
```  
  
### <a name="remarks"></a>Comentarios  
 Agregar esta macro para el objeto si recibe el mensaje de error del compilador `GetControllingUnknown` no está definido (por ejemplo, en **CComAggregateCreator**).  
  
##  <a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE  
 Especifica que no se puede agregar el objeto.  
  
```
DECLARE_NOT_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre del objeto de clase que se va a definir como no agregable.  
  
### <a name="remarks"></a>Comentarios  
 `DECLARE_NOT_AGGREGATABLE`hace que `CreateInstance` para devolver un error ( **CLASS_E_NOAGGREGATION**) si se realiza un intento para agregado en el objeto.  
  
 De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene el [DECLARE_AGGREGATABLE](#declare_aggregatable) macro, que especifica que se puede agregar el objeto. Para invalidar este comportamiento predeterminado, incluya `DECLARE_NOT_AGGREGATABLE` en la definición de clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE  
 Especifica que debe agregarse el objeto.  
  
```
DECLARE_ONLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre del objeto de clase está definiendo como solo agregables.  
  
### <a name="remarks"></a>Comentarios  
 `DECLARE_ONLY_AGGREGATABLE`se produce un error ( **E_FAIL**) si se realiza un intento para **CoCreate** el objeto como objeto.  
  
 De forma predeterminada, [CComCoClass](../../atl/reference/ccomcoclass-class.md) contiene el [DECLARE_AGGREGATABLE](#declare_aggregatable) macro, que especifica que se puede agregar el objeto. Para invalidar este comportamiento predeterminado, incluya `DECLARE_ONLY_AGGREGATABLE` en la definición de clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]  
  
##  <a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE  
 Especifica que una instancia de **CComPolyObject \<**  *x*  **>**  se crea cuando se crea el objeto.  
  
```
DECLARE_POLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre del objeto de clase está definiendo como agregable o no es agregable.  
  
### <a name="remarks"></a>Comentarios  
 Durante la creación, se comprueba el valor del objeto desconocido externo. Si es **NULL**, **IUnknown** se implementa para un objeto no agregado. Si no se encuentra el desconocido externo **NULL**, **IUnknown** se implementa para un objeto agregado.  
  
 La ventaja de usar `DECLARE_POLY_AGGREGATABLE` es evitar tener ambos `CComAggObject` y `CComObject` en su módulo para controlar los casos agregados y no agregados. Una sola `CComPolyObject` objeto controla ambos casos. Esto significa que existen solo una copia de la tabla vtable y una copia de las funciones del módulo. Si su tabla vtable es grande, esto puede reducir considerablemente el tamaño del módulo. Sin embargo, si su tabla vtable es pequeña, usando `CComPolyObject` puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, como son `CComAggObject` y `CComObject`.  
  
 El `DECLARE_POLY_AGGREGATABLE` macro automáticamente se declara en el objeto si usa el Asistente para controles ATL para crear un control total.  
  
##  <a name="declare_protect_final_construct"></a>MACRO DECLARE_PROTECT_FINAL_CONSTRUCT  

 Impide que el objeto se está eliminando si (durante [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) el objeto agregado interno incrementa el recuento de referencias, a continuación, disminuye el recuento a 0.  
  
```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```  
  
##  <a name="declare_view_status"></a>DECLARE_VIEW_STATUS  
 Colocar esta macro en la clase de control de un control ActiveX ATL para especificar el **VIEWSTATUS** marcas para el contenedor.  
  
```
DECLARE_VIEW_STATUS( statusFlags )
```  
  
### <a name="parameters"></a>Parámetros  
 `statusFlags`  
 [in] El **VIEWSTATUS** marcas. Vea [VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201) para obtener una lista de marcas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)
