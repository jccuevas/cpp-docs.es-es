---
title: CObject (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
dev_langs:
- C++
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38c27d2fa0e04770bae69901e1164da84c2186ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377245"
---
# <a name="cobject-class"></a>CObject (clase)
La clase base principal para la biblioteca de MFC (Microsoft Foundation Class).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class AFX_NOVTABLE CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObject::CObject](#cobject)|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObject:: AssertValid](#assertvalid)|Valida la integridad de este objeto.|  
|[CObject::Dump](#dump)|Realiza un volcado de diagnóstico de este objeto.|  
|[CObject::GetRuntimeClass](#getruntimeclass)|Devuelve el `CRuntimeClass` estructura correspondiente a la clase de este objeto.|  
|[CObject:: IsKindOf](#iskindof)|Comprueba la relación de este objeto para una clase determinada.|  
|[CObject::IsSerializable](#isserializable)|Comprueba si este objeto se puede serializar.|  
|[CObject:: Serialize](#serialize)|Carga o almacena un objeto del usuario o para un archivo.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Eliminación de CObject::operator](#operator_delete)|Especial **eliminar** operador.|  
|[CObject::operator nueva](#operator_new)|Especial **nueva** operador.|  
  
## <a name="remarks"></a>Comentarios  
 Que actúa como la raíz no solo para las clases de biblioteca como `CFile` y `CObList`, sino también para las clases que se escribe. `CObject` Proporciona los servicios básicos, incluidos  
  
-   Compatibilidad con la serialización  
  
-   Información de clase en tiempo de ejecución  
  
-   Resultados de diagnóstico de objeto  
  
-   Compatibilidad con las clases de colección  
  
 Tenga en cuenta que `CObject` no se admite la herencia múltiple. Las clases derivadas pueden tener solo una `CObject` clase base y que `CObject` debe estar situado en la jerarquía. Sin embargo, está permitido, tienen estructuras y no- `CObject`-clases derivadas en bifurcaciones de herencia múltiple derecho.  
  
 Se dará cuenta de las ventajas principales de `CObject` si utiliza algunas de las macros opcionales de la implementación de la clase y las declaraciones de derivación.  
  
 Las macros de primer nivel, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) y [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), permitir el acceso de tiempo de ejecución para el nombre de clase y su posición en la jerarquía. Esto, a su vez, permite volcar diagnóstico significativos.  
  
 Las macros de segundo nivel, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), incluir toda la funcionalidad de las macros de primer nivel y permiten que un objeto "serializará" hacia y desde un "archivo".  
  
 Para obtener información sobre cómo derivar clases de C++ y Microsoft Foundation classes en general y usar `CObject`, consulte [usar CObject](../../mfc/using-cobject.md) y [serialización](../../mfc/serialization-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="assertvalid"></a>  CObject:: AssertValid  
 Valida la integridad de este objeto.  
  
```  
virtual void AssertValid() const;  
```  
  
### <a name="remarks"></a>Comentarios  
 `AssertValid` realiza una comprobación de validez de este objeto y comprueba su estado interno. En la versión de depuración de la biblioteca de `AssertValid` puede declara una aserción y, por tanto, finalizar el programa con un mensaje que indica el número de línea y el nombre de archivo donde la aserción.  
  
 Al escribir su propia clase, debe invalidar el `AssertValid` función para proporcionar servicios de diagnóstico para usted mismo y a otros usuarios de la clase. Reemplazados `AssertValid` llama normalmente el `AssertValid` función de su clase base antes de proteger los miembros de datos únicos para la clase derivada.  
  
 Dado que `AssertValid` es un **const** función, no se permite cambiar el estado del objeto durante la prueba. Su propia clase derivada `AssertValid` funciones no deben producir excepciones, pero en su lugar debe imponer si detectan los datos de objeto no válido.  
  
 La definición de "validez" depende de la clase del objeto. Como regla general, la función debe realizar una "comprobación superficial". Es decir, si un objeto contiene punteros a otros objetos, debe comprobar para ver si los punteros no son nulos, pero no debería realizar pruebas en los objetos que hace referencia a los punteros de validez.  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los `CObject` ejemplos.  
  
 [!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]  
  
 Para obtener otro ejemplo, vea [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).  
  
##  <a name="cobject"></a>  CObject::CObject  
 Estas funciones son el estándar `CObject` constructores.  
  
```  
CObject();  
CObject(const CObject& objectSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *objectSrc*  
 Una referencia a otro `CObject`  
  
### <a name="remarks"></a>Comentarios  
 El constructor de la clase derivada llama automáticamente a la versión predeterminada.  
  
 Si la clase es serializable (que incorpora el `IMPLEMENT_SERIAL` macro), debe tener un constructor predeterminado (un constructor sin argumentos) en la declaración de clase. Si no tiene un constructor predeterminado, declare privado o protegido constructor "vacío". Para obtener más información, consulte [CObject utilizando](../../mfc/using-cobject.md).  
  
 El constructor de copia estándar de C++ predeterminado clase hace una copia miembro a miembro. La presencia de privado `CObject` constructor de copias garantiza un mensaje de error del compilador si el constructor de copias de la clase es necesaria, pero no está disponible. Por lo tanto, debe proporcionar un constructor de copias si su clase necesita esta capacidad.  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en el `CObject` ejemplos.  
  
 [!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]  
  
##  <a name="dump"></a>  CObject::Dump  
 Vuelca el contenido del objeto para un [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objeto.  
  
```  
virtual void Dump(CDumpContext& dc) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dc`  
 El contexto de volcado de diagnóstico para volcar, normalmente `afxDump`.  
  
### <a name="remarks"></a>Comentarios  
 Al escribir su propia clase, debe invalidar el `Dump` función para proporcionar servicios de diagnóstico para usted mismo y a otros usuarios de la clase. Reemplazados `Dump` llama normalmente el `Dump` función de su clase base antes de imprimir los miembros de datos únicos para la clase derivada. `CObject::Dump` Imprime el nombre de clase si la clase utiliza el `IMPLEMENT_DYNAMIC` o `IMPLEMENT_SERIAL` macro.  
  
> [!NOTE]
>  Su `Dump` función debe imprimir un carácter de nueva línea al final de su salida.  
  
 `Dump` llamadas tienen sentido sólo en la versión de depuración de la biblioteca Microsoft Foundation Class. Debe poner entre corchetes llamadas, las declaraciones de función y las implementaciones de funciones con **#ifdef _DEBUG** /  `#endif` instrucciones de compilación condicional.  
  
 Puesto que `Dump` es un **const** función, no se permite cambiar el estado del objeto durante el volcado de memoria.  
  
 El [CDumpContext inserción (<<) operador](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) llamadas `Dump` cuando un `CObject` se inserta el puntero.  
  
 `Dump` permite solo "acíclico" volcado de objetos. Por ejemplo, se puede volcar una lista de objetos, pero si uno de los objetos es la propia lista, finalmente se desborde la pila.  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los `CObject` ejemplos.  
  
 [!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]  
  
##  <a name="getruntimeclass"></a>  CObject::GetRuntimeClass  
 Devuelve el `CRuntimeClass` estructura correspondiente a la clase de este objeto.  
  
```  
virtual CRuntimeClass* GetRuntimeClass() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura correspondiente a la clase de este objeto; nunca **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Hay un `CRuntimeClass` estructura para cada `CObject`-clase derivada. Los miembros de estructura son los siguientes:  
  
- **LPCSTR m_lpszClassName** una cadena terminada en null que contiene el nombre de clase de ASCII.  
  
- **int m_nObjectSize** el tamaño del objeto, en bytes. Si el objeto tiene miembros de datos que señalan a la memoria asignada, no se incluye el tamaño de la memoria.  
  
- **UINT m_wSchema** el número de esquema (-1 para las clases de objetos no serializables). Consulte la [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro para obtener una descripción del número de esquema.  
  
- **CObject\* (PASCAL\* m_pfnCreateObject) ()** un puntero a función al constructor predeterminado que crea un objeto de la clase (válido únicamente si la clase admite la creación dinámica; en caso contrario, devuelve **NULL** ).  
  
- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) ()** si la aplicación se vincula dinámicamente a la versión AFXDLL de MFC, un puntero a una función que devuelve el `CRuntimeClass` estructura de la clase base.  
  
- **CRuntimeClass\* m_pBaseClass** si la aplicación está vinculada estáticamente a MFC, un puntero a la `CRuntimeClass` estructura de la clase base.  
  
 Esta función requiere el uso de la [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate), o [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro en la implementación de la clase. En caso contrario, obtendrá resultados incorrectos.  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los `CObject` ejemplos.  
  
 [!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]  
  
##  <a name="iskindof"></a>  CObject:: IsKindOf  
 Comprueba la relación de este objeto para una clase determinada.  
  
```  
BOOL IsKindOf(const CRuntimeClass* pClass) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pClass`  
 Un puntero a un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura asociada con su `CObject`-clase derivada.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se corresponde con la clase; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función comprueba `pClass` para ver si (1) es un objeto de la clase especificada o (2) no es un objeto de una clase derivada de la clase especificada. Esta función solo funciona para las clases que se declara con el [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate), o [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro.  
  
 No utilice esta función ampliamente porque se frustra la característica de polimorfismo de C++. Utilice las funciones virtuales en su lugar.  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los `CObject` ejemplos.  
  
 [!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]  
  
##  <a name="isserializable"></a>  CObject::IsSerializable  
 Comprueba si este objeto es apto para la serialización.  
  
```  
BOOL IsSerializable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se puede serializar este objeto; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para que una clase que sean serializables, su declaración debe contener el [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro y la implementación deben contener la [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro.  
  
> [!NOTE]
>  No se invalidan esta función.  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los `CObject` ejemplos.  
  
 [!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]  
  
##  <a name="operator_delete"></a>  Eliminación de CObject::operator  
 Para la versión de lanzamiento de la biblioteca de operador **eliminar** libera la memoria asignada por el operador **nueva**.  
  
```  
void PASCAL operator delete(void* p);

 
void PASCAL operator delete(
    void* p,
    void* pPlace);

 
void PASCAL operator delete(
    void* p,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>Comentarios  
 En la versión de depuración, operador **eliminar** participa en un esquema de asignación de supervisión diseñado para detectar pérdidas de memoria.  
  
 Si usa la línea de código  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 antes de cualquiera de sus implementaciones en una. CPP Archivo, a continuación, la tercera versión de **eliminar** se usará, almacenar el nombre de archivo y número de línea en el bloque asignado para la creación posterior de informes. No tiene que preocuparse sobre cómo proporcionar los parámetros adicionales; una macro se encarga de para usted.  
  
 Aunque no use `DEBUG_NEW` en modo de depuración, se sigue obteniendo la detección de pérdidas, pero sin los informes de número de línea del archivo de código fuente se ha descrito anteriormente.  
  
 Si se anulan los operadores de **nueva** y **eliminar**, pierda esta capacidad de diagnóstico.  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en el `CObject` ejemplos.  
  
 [!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]  
  
##  <a name="operator_new"></a>  CObject::operator nueva  
 Para la versión de lanzamiento de la biblioteca de operador **nueva** realiza una asignación óptima de memoria de una manera similar a `malloc`.  
  
```  
void* PASCAL operator new(size_t nSize);  
void* PASCAL operator new(size_t, void* p);

 
void* PASCAL operator new(
    size_t nSize,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>Comentarios  
 En la versión de depuración, operador **nueva** participa en un esquema de asignación de supervisión diseñado para detectar pérdidas de memoria.  
  
 Si usa la línea de código  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 antes de cualquiera de sus implementaciones en una. CPP Archivo, a continuación, la segunda versión de **nueva** se usará, almacenar el nombre de archivo y número de línea en el bloque asignado para la creación posterior de informes. No tiene que preocuparse sobre cómo proporcionar los parámetros adicionales; una macro se encarga de para usted.  
  
 Aunque no use `DEBUG_NEW` en modo de depuración, se sigue obteniendo la detección de pérdidas, pero sin los informes de número de línea del archivo de código fuente se ha descrito anteriormente.  
  
> [!NOTE]
>  Si invalida este operador, también debe invalidar **eliminar**. No utilice la biblioteca estándar de **_new_handler** (función).  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en el `CObject` ejemplos.  
  
 [!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]  
  
##  <a name="serialize"></a>  CObject:: Serialize  
 Lee o escribe este objeto de o en un archivo.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 `ar`  
 Un `CArchive` objeto que se va a serializar a o desde.  
  
### <a name="remarks"></a>Comentarios  
 Debe invalidar `Serialize` para cada clase que se va a serializar. Reemplazados `Serialize` debe llamar primero a la `Serialize` función de su clase base.  
  
 También debe utilizar el [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) debe utilizar la macro en la declaración de clase así como el [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro en la implementación.  
  
 Use [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) o [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) para determinar si el archivo se carga o almacenamiento.  
  
 `Serialize` llama a [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) y [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Estas funciones están asociadas a la `CArchive` operador de inserción ( **< \<**) y el operador de extracción ( **>>**).  
  
 Para obtener ejemplos de serialización, vea el artículo [serialización: serializar un objeto](../../mfc/serialization-serializing-an-object.md).  
  
### <a name="example"></a>Ejemplo  
 Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de los `CAge` clase usada en todos los `CObject` ejemplos.  
  
 [!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



