---
title: CArchive (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- I/O [MFC], archiving objects
- CArchive class
- serialization [C++], CArchive class
- storage [C++], CArchive class
- data storage [C++], CArchive class
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 501b365678a45148aabe638ff341f3ae995e4ab5
ms.lasthandoff: 02/24/2017

---
# <a name="carchive-class"></a>CArchive (clase)
Permite guardar una red compleja de objetos en un formato binario permanente (normalmente almacenamiento en disco) que se conserva después de que se eliminen esos objetos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CArchive  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CArchive::CArchive](#carchive)|Crea un objeto `CArchive`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CArchive::Abort](#abort)|Cierra un archivo sin producir una excepción.|  
|[CArchive::Close](#close)|Vacía los datos no escritos y desconecta el `CFile`.|  
|[CArchive::Flush](#flush)|Vacía los datos no escritos desde el búfer de archivo.|  
|[CArchive::GetFile](#getfile)|Obtiene el `CFile` puntero de objeto para este archivo.|  
|[CArchive::GetObjectSchema](#getobjectschema)|Llamar desde el `Serialize` función para determinar la versión del objeto que se está deserializando.|  
|[CArchive::IsBufferEmpty](#isbufferempty)|Determina si el búfer se ha vaciado Sockets de Windows durante el proceso de recepción.|  
|[CArchive::IsLoading](#isloading)|Determina si se está cargando el archivo.|  
|[CArchive::IsStoring](#isstoring)|Determina si se almacena el archivo.|  
|[CArchive::MapObject](#mapobject)|Coloca los objetos en la asignación que no se serializan en el archivo, pero que están disponibles para los objetos secundarios para hacer referencia a.|  
|[CArchive::Read](#read)|Lee los bytes sin formato.|  
|[CArchive::ReadClass](#readclass)|Lecturas previamente almacena una referencia de clase con `WriteClass`.|  
|[CArchive::ReadObject](#readobject)|Llama a un objeto `Serialize` función para cargar.|  
|[CArchive::ReadString](#readstring)|Lee una sola línea de texto.|  
|[CArchive::SerializeClass](#serializeclass)|Lee o escribe la referencia de clase a la `CArchive` objeto según la dirección de la `CArchive`.|  
|[CArchive::SetLoadParams](#setloadparams)|Establece el tamaño al que crece la carga de matriz. Debe llamarse antes de carga cualquier objeto o antes de `MapObject` o `ReadObject` se llama.|  
|[CArchive::SetObjectSchema](#setobjectschema)|Establece el esquema de objetos almacenado en el objeto de almacenamiento.|  
|[CArchive::SetStoreParams](#setstoreparams)|Establece el tamaño de la tabla hash y el tamaño del bloque de la asignación que se utiliza para identificar objetos únicos durante el proceso de serialización.|  
|[CArchive:: Write](#write)|Escribe los bytes sin formato.|  
|[CArchive::WriteClass](#writeclass)|Escribe una referencia a la `CRuntimeClass` a la `CArchive`.|  
|[CArchive::WriteObject](#writeobject)|Llama a un objeto `Serialize` función para el almacenamiento.|  
|[CArchive::WriteString](#writestring)|Escribe una sola línea de texto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CArchive::operator&lt;&lt;](#operator_lt_lt)|Almacena los objetos y tipos primitivos al archivo.|  
|[CArchive::operator&gt;&gt;](#operator_gt_gt)|Carga los objetos y tipos primitivos del archivo.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CArchive::m_pDocument](#m_pdocument)||  
  
## <a name="remarks"></a>Comentarios  
 `CArchive`no tiene una clase base.  
  
 Más adelante puede cargar los objetos de almacenamiento persistente, reconstituir a ellos en la memoria. Este proceso de hacer que los datos persistentes se denomina "serialización".  
  
 Puede pensar en un objeto de almacenamiento como una especie de secuencia binaria. Como un flujo de entrada y salida, un archivo está asociado a un archivo y permite la escritura almacenada en búfer y lectura de datos a y desde el almacenamiento. Una secuencia de entrada y salida procesa secuencias de caracteres ASCII, pero un archivo procesa los datos de objeto binario en un formato no redundante y eficaz.  
  
 Debe crear un [CFile](../../mfc/reference/cfile-class.md) objeto antes de poder crear un `CArchive` objeto. Además, debe asegurarse de que el estado de carga o almacenamiento de archivado es compatible con el modo del archivo abierto. Está limitado a un archivo activo por archivo.  
  
 Cuando se construye un `CArchive` de objeto, se adjunta a un objeto de clase `CFile` (o una clase derivada) que representa un archivo abierto. También especifica si se usará para cargar o almacenar el archivo. Un `CArchive` objeto puede procesar no sólo los tipos primitivos, pero también los objetos de [CObject](../../mfc/reference/cobject-class.md)-diseñadas para la serialización de clases derivadas. Una clase serializable normalmente tiene un `Serialize` función miembro y se utiliza normalmente la [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macros, como se describe en la clase `CObject`.  
  
 La extracción sobrecargada ( ** >> **) y la inserción ( ** << **) operadores son interfaces de programación de archivo adecuada que admiten ambos tipos primitivos y `CObject`-las clases derivadas.  
  
 `CArchive`también admite la programación con las clases de Windows Sockets de MFC [CSocket](../../mfc/reference/csocket-class.md) y [CSocketFile](../../mfc/reference/csocketfile-class.md). El [IsBufferEmpty](#isbufferempty) función miembro es compatible con dicho uso.  
  
 Para obtener más información sobre `CArchive`, consulte los artículos [serialización](../../mfc/serialization-in-mfc.md) y [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CArchive`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="a-nameaborta--carchiveabort"></a><a name="abort"></a>CArchive::Abort  
 Llame a esta función para cerrar el archivo sin producir una excepción.  
  
```  
void Abort ();
```  
  
### <a name="remarks"></a>Comentarios  
 El **CArchive** destructor normalmente llamará **cerrar**, lo que hará que vacíe todos los datos que no se ha guardado al objeto asociado `CFile` objeto. Esto puede producir excepciones.  
  
 Al capturar estas excepciones, es una buena idea usar **anular**, de modo que destruir la `CArchive` objeto no hace aún más las excepciones. Cuando el control de excepciones, `CArchive::Abort` no producirá una excepción en errores porque, a diferencia [CArchive::Close](#close), **anular** omite los errores.  
  
 Si usó **nueva** para asignar la `CArchive` objeto en el montón, debe eliminar después de cerrar el archivo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CArchive::WriteClass](#writeclass).  
  
##  <a name="a-namecarchivea--carchivecarchive"></a><a name="carchive"></a>CArchive::CArchive  
 Construye un `CArchive` de objeto y especifica si se utilizará para cargar o almacenar los objetos.  
  
```  
CArchive(
    CFile* pFile,  
    UINT nMode,  
    int nBufSize = 4096,  
    void* lpBuf = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFile`  
 Un puntero a la `CFile` objeto que es el último origen o destino de los datos persistentes.  
  
 `nMode`  
 Una marca que especifica si los objetos se cargan desde o se almacena en el archivo. El `nMode` parámetro debe tener uno de los siguientes valores:  
  
- **CArchive::load** carga los datos del archivo. Sólo requiere `CFile` permiso de lectura.  
  
- **CArchive::store** guarda los datos en el archivo. Requiere `CFile` permiso de escritura.  
  
- **CArchive::bNoFlushOnDelete** impide que el archivo automáticamente una llamada a `Flush` cuando se llama al destructor de archivo. Si establece esta marca, usted es responsable de llamar explícitamente a **cerrar** antes de que se llama al destructor. Si no lo hace, se dañarán los datos.  
  
 `nBufSize`  
 Un entero que especifica el tamaño del búfer interno del archivo, en bytes. Tenga en cuenta que el tamaño de búfer predeterminado es de 4.096 bytes. Si archiva habitualmente objetos grandes, se mejorará el rendimiento si utiliza un tamaño de búfer mayor que es un múltiplo del tamaño de búfer del archivo.  
  
 `lpBuf`  
 Un puntero a un búfer proporcionado por el usuario de tamaño opcional `nBufSize`. Si no se especifica este parámetro, el archivo asigna un búfer desde el montón local y libera cuando se destruye el objeto. El archivo no liberar un búfer proporcionado por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 No se puede cambiar esta especificación después de haber creado el archivo.  
  
 No se puede usar `CFile` operaciones para modificar el estado del archivo hasta que haya cerrado el archivo. Cualquier operación de esta clase puede dañar la integridad del archivo. Puede tener acceso a la posición del puntero de archivo en cualquier momento durante la serialización, se obtiene el objeto de archivo del archivo de la [GetFile](#getfile) función miembro y, a continuación, utilizar el [CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition) (función). Debe llamar a [CArchive::Flush](#flush) antes de obtener la posición del puntero de archivo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#12;](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]  
  
##  <a name="a-nameclosea--carchiveclose"></a><a name="close"></a>CArchive::Close  
 Vacía los datos permanecen en el búfer, se cierra el archivo y se desconecta el archivo desde el archivo.  
  
```  
void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 No se permite ninguna otra operación en el archivo. Después de cerrar un archivo, puede crear otro archivo para el mismo archivo o puede cerrar el archivo.  
  
 La función miembro **cerrar** garantiza que todos los datos se transfieren desde el archivo para el archivo y hace que el archivo no está disponible. Para completar la transferencia del archivo en el medio de almacenamiento, primero debe usar [CFile::Close](../../mfc/reference/cfile-class.md#close) y, a continuación, destruya el `CFile` objeto.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CArchive::WriteString](#writestring).  
  
##  <a name="a-nameflusha--carchiveflush"></a><a name="flush"></a>CArchive::Flush  
 Obliga a todos los datos permanecen en el búfer de almacenamiento se escriban en el archivo.  
  
```  
void Flush();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro `Flush` garantiza que todos los datos se transfieren desde el archivo en el archivo. Se debe llamar a [CFile::Close](../../mfc/reference/cfile-class.md#close) para completar la transferencia del archivo en el medio de almacenamiento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#13;](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]  
  
##  <a name="a-namegetfilea--carchivegetfile"></a><a name="getfile"></a>CArchive::GetFile  
 Obtiene el `CFile` puntero de objeto para este archivo.  
  
```  
CFile* GetFile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero constante a la `CFile` objeto en uso.  
  
### <a name="remarks"></a>Comentarios  
 Debe vaciar el archivo antes de utilizar `GetFile`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#14;](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]  
  
##  <a name="a-namegetobjectschemaa--carchivegetobjectschema"></a><a name="getobjectschema"></a>CArchive::GetObjectSchema  
 Llame a esta función desde el `Serialize` función para determinar la versión del objeto que se está deserializando.  
  
```  
UINT GetObjectSchema();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Durante la deserialización, la versión del objeto que se va a leer.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a esta función solo es válida cuando la `CArchive` objeto se está cargando ( [CArchive::IsLoading](#isloading) devuelve distinto de cero). Debe ser la primera llamada en el `Serialize` función y llamada solo una vez. Un valor devuelto de ( **UINT**) -1 indica que el número de versión es desconocido.  
  
 Un `CObject`-clase derivada puede usar **VERSIONABLE_SCHEMA** combinado (bit a bit con `OR`) con la versión del esquema (en el `IMPLEMENT_SERIAL` (macro)) para crear un "objeto versionable", es decir, un objeto cuyo `Serialize` función miembro puede leer varias versiones. La funcionalidad del marco predeterminado (sin **VERSIONABLE_SCHEMA**) es producir una excepción cuando la versión no coincide.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#15;](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]  
  
##  <a name="a-nameisbufferemptya--carchiveisbufferempty"></a><a name="isbufferempty"></a>CArchive::IsBufferEmpty  
 Llame a esta función miembro para determinar si el búfer interno del objeto de archivo está vacío.  
  
```  
BOOL IsBufferEmpty() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el búfer del archivo de almacenamiento está vacía. en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se proporciona para permitir la programación con la clase de Windows Sockets de MFC `CSocketFile`. No es necesario utilizar un archivo asociado con un `CFile` objeto.  
  
 La razón para usar `IsBufferEmpty` con un archivo asociado con un `CSocketFile` objeto es que el búfer del archivo de almacenamiento podría contener más de un mensaje o registro. Después de recibir un mensaje, debe usar `IsBufferEmpty` para controlar un bucle que continúa recibiendo datos hasta que el búfer está vacío. Para obtener más información, consulte el [recepción](../../mfc/reference/casyncsocket-class.md#receive) función miembro de clase `CAsyncSocket`, que muestra cómo utilizar `IsBufferEmpty`.  
  
 Para obtener más información, consulte [Windows Sockets: usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="a-nameisloadinga--carchiveisloading"></a><a name="isloading"></a>CArchive::IsLoading  
 Determina si el archivo está cargando datos.  
  
```  
BOOL IsLoading() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el archivo se está usando actualmente para la carga; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llama a esta función miembro la `Serialize` las funciones de las clases de archivado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization Nº&16;](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]  
  
##  <a name="a-nameisstoringa--carchiveisstoring"></a><a name="isstoring"></a>CArchive::IsStoring  
 Determina si el archivo es almacenar los datos.  
  
```  
BOOL IsStoring() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el archivo se está usando actualmente para almacenar; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llama a esta función miembro la `Serialize` las funciones de las clases de archivado.  
  
 Si el `IsStoring` estado de un archivo es distinto de cero, entonces su `IsLoading` estado es 0 y viceversa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#17;](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]  
  
##  <a name="a-namemapobjecta--carchivemapobject"></a><a name="mapobject"></a>CArchive::MapObject  
 Llame a esta función miembro para colocar en el mapa que realmente no se serializan en el archivo, pero que están disponibles para los objetos secundarios para hacer referencia a los objetos.  
  
```  
void MapObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>Parámetros  
 `pOb`  
 Puntero constante al objeto que se almacena.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, no puede serializar un documento, pero podría serializar los elementos que forman parte del documento. Llamando a `MapObject`, permite que los elementos o subobjetos, para hacer referencia al documento. Además, pueden serializar los subelementos serializados sus `m_pDocument` puntero.  
  
 Puede llamar a `MapObject` al almacenar y cargar desde el `CArchive` objeto. `MapObject`Agrega el objeto especificado a las estructuras de datos interna mantenidas por el `CArchive` objeto durante la serialización y deserialización, pero a diferencia de [ReadObject](#readobject) y [WriteObject](#writeobject)**,** , no llamar a serializar en el objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#18;](../../mfc/codesnippet/cpp/carchive-class_7.h)]  
  
 [!code-cpp[NVC_MFCSerialization Nº&19;](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]  
  
 [!code-cpp[NVC_MFCSerialization&#20;](../../mfc/codesnippet/cpp/carchive-class_9.h)]  
  
 [!code-cpp[21 NVC_MFCSerialization](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]  
  
##  <a name="a-namempdocumenta--carchivempdocument"></a><a name="m_pdocument"></a>CArchive::m_pDocument  
 Establecido en **NULL** de forma predeterminada, este puntero a un **CDocument** se puede establecer en cualquier valor al usuario de la `CArchive` deseos de instancia.  
  
```  
CDocument* m_pDocument;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un uso común de este puntero es a transmitir información adicional acerca del proceso de serialización para todos los objetos que se está serializando. Esto se logra al inicializar el puntero con el documento (una **CDocument**-clase derivada) que se está serializando, de tal forma que los objetos dentro del documento pueden tener acceso al documento si es necesario. También usa este puntero `COleClientItem` objetos durante la serialización.  
  
 Los conjuntos de framework `m_pDocument` al documento que se está serializando cuando un usuario ejecuta un archivo, abrir o guardar comandos. Si se serializa un documento de contenedor de vinculación e incrustación de objetos (OLE) por motivos distintos a abrir o guardar, debe establecer explícitamente `m_pDocument`. Por ejemplo, podría hacerlo al serializar un documento contenedor en el Portapapeles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#35;](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]  
  
##  <a name="a-nameoperatorltlta--carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>CArchive::operator&lt;&lt;  
 Almacena el objeto indicado o un tipo primitivo al archivo.  
  
```  
friend CArchive& operator<<(
    CArchive& ar,  
    const CObject* pOb);

 
throw(
    CArchiveException*, 
    CFileException*);

 
CArchive& AFXAPI operator<<(
    CArchive& ar,  
    const RECT& rect);

 
CArchive& AFXAPI operator<<(
    CArchive& ar,  
    POINT point);

 
CArchive& AFXAPI operator<<(
    CArchive& ar,  
    SIZE size);

 
template<typename BaseType,  
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,  
    StringTraits>& str);  
  
CArchive& operator<<(BYTE by); 
CArchive& operator<<(WORD w); 
CArchive& operator<<(LONG l); 
CArchive& operator<<(DWORD dw); 
CArchive& operator<<(float f); 
CArchive& operator<<(double d); 
CArchive& operator<<(int i); 
CArchive& operator<<(short w); 
CArchive& operator<<(char ch); 
CArchive& operator<<(wchar_t ch); 
CArchive& operator<<(unsigned u); 
CArchive& operator<<(bool b); 
CArchive& operator<<(ULONGLONG dwdw); 
CArchive& operator<<(LONGLONG dwdw);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CArchive` referencia que permite varios operadores de inserción en una sola línea.  
  
### <a name="remarks"></a>Comentarios  
 Las dos últimas versiones anteriores son específicamente para almacenar números enteros de 64 bits.  
  
 Si ha usado la `IMPLEMENT_SERIAL` macro en su implementación de la clase y, a continuación, el operador de inserción sobrecargado para `CObject` llama al método protegido **WriteObject**. A su vez, llama a esta función, la `Serialize` función de la clase.  
  
 El [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (operador de inserción<) supports diagnostic dumping and storing to an archive. supports="" diagnostic="" dumping="" and="" storing="" to="" an=""></) supports diagnostic dumping and storing to an archive.>  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra el uso de la `CArchive` operador de inserción < with="" the=""> `int` y `long` tipos.  
  
 [!code-cpp[NVC_MFCSerialization&#31;](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo 2 muestra el uso de la `CArchive` operador de inserción < with="" the=""> `CStringT` tipo.  
  
 [!code-cpp[NVC_MFCSerialization&#32;](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]  
  
##  <a name="a-nameoperatorgtgta--carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>CArchive::operator&gt;&gt;  
 Carga el objeto indicado o un tipo primitivo del archivo.  
  
```  
friend CArchive& operator>>(
    CArchive& ar,  
    CObject *& pOb);

 
throw(
    CArchiveException*, 
    CFileException*, 
    CMemoryException*);

 
friend CArchive& operator>>(
    CArchive& ar,  
    const CObject *& pOb);

 
throw(
    CArchiveException*, 
    CFileException*, 
    CMemoryException*);

 
CArchive& AFXAPI operator>>(
    CArchive& ar,  
    const RECT& rect);

 
CArchive& AFXAPI operator>>(
    CArchive& ar,  
    POINT point);

 
CArchive& AFXAPI operator>>(
    CArchive& ar,  
    SIZE size);

 
template<typename BaseType,  
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType, 
    StringTraits>& str);  
  
CArchive& operator>>(BYTE& by);    
CArchive& operator>>(WORD& w);    
CArchive& operator>>(int& i);    
CArchive& operator>>(LONG& l);    
CArchive& operator>>(DWORD& dw);    
CArchive& operator>>(float& f);    
CArchive& operator>>(double& d);    
CArchive& operator>>(short& w);    
CArchive& operator>>(char& ch);    
CArchive& operator>>(wchar_t& ch);    
CArchive& operator>>(unsigned& u);    
CArchive& operator>>(bool& b);    
CArchive& operator>>(ULONGLONG& dwdw);   
CArchive& operator>>(LONGLONG& dwdw);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CArchive` referencia que permite varios operadores de extracción en una sola línea.  
  
### <a name="remarks"></a>Comentarios  
 Las dos últimas versiones anteriores son específicamente para cargar los enteros de 64 bits.  
  
 Si ha usado la `IMPLEMENT_SERIAL` macro en su implementación de la clase y, a continuación, los operadores de extracción sobrecargados para `CObject` llamada protegido **ReadObject** función (con un puntero de la clase de tiempo de ejecución distinto de cero). A su vez, llama a esta función, la `Serialize` función de la clase.  
  
 El [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) extracción > (operador) admite la carga de un archivo.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra el uso de la `CArchive` operador de extracción >> con el `int` tipo.  
  
 [!code-cpp[NVC_MFCSerialization Nº&33;](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra el uso de la `CArchive` operadores de inserción y extracción \< y >> con el `CStringT` tipo.  
  
 [!code-cpp[NVC_MFCSerialization&#34;](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]  
  
##  <a name="a-namereada--carchiveread"></a><a name="read"></a>CArchive::Read  
 Lee un número especificado de bytes del archivo.  
  
```  
UINT Read(void* lpBuf, UINT nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuf`  
 Un puntero a un búfer proporcionado por el usuario que va a recibir los datos leídos desde el archivo.  
  
 `nMax`  
 Un entero sin signo especifica el número de bytes para leer desde el archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero sin signo que contiene el número de bytes leídos realmente. Si el valor devuelto es menor que el número solicitado, se alcanzó el final del archivo. Se inicia ninguna excepción en la condición de final de archivo.  
  
### <a name="remarks"></a>Comentarios  
 El archivo no interpreta los bytes.  
  
 Puede usar el **lectura** función miembro dentro de su `Serialize` función para leer estructuras normales que se encuentran en los objetos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#24;](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]  
  
##  <a name="a-namereadclassa--carchivereadclass"></a><a name="readclass"></a>CArchive::ReadClass  
 Llame a esta función miembro para obtener una referencia a una clase almacenada previamente con [WriteClass](#writeclass).  
  
```  
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,  
    UINT* pSchema = NULL,  
    DWORD* pObTag = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pClassRefRequested`  
 Un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura que corresponde a la referencia de la clase solicitada. Puede ser **NULL**.  
  
 `pSchema`  
 Puntero a un esquema de la clase en tiempo de ejecución que se almacenó previamente.  
  
 `pObTag`  
 Un número que hace referencia a la etiqueta de un objeto único. Utilizado internamente por la implementación de [ReadObject](#readobject). Expuesto para programación avanzada `pObTag` normalmente debería ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura.  
  
### <a name="remarks"></a>Comentarios  
 Si `pClassRefRequested` no **NULL**, `ReadClass` comprueba que la información de clase archivada es compatible con la clase en tiempo de ejecución. Si no es compatible, `ReadClass` producirá un [CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Debe usar la clase en tiempo de ejecución [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); en caso contrario, `ReadClass` producirá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Si `pSchema` es **NULL**, se puede recuperar el esquema de la clase almacenado llamando a [CArchive::GetObjectSchema](#getobjectschema); en caso contrario, ** \* ** `pSchema` contendrá el esquema de la clase de tiempo de ejecución que estaba almacenado previamente.  
  
 Puede usar [SerializeClass](#serializeclass) en lugar de `ReadClass`, que controla la lectura y escritura de la referencia de clase.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CArchive::WriteClass](#writeclass).  
  
##  <a name="a-namereadobjecta--carchivereadobject"></a><a name="readobject"></a>CArchive::ReadObject  
 Lee datos del objeto desde el archivo y crea un objeto del tipo adecuado.  
  
```  
CObject* ReadObject(const CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>Parámetros  
 `pClass`  
 Un puntero constante a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura que corresponde al objeto de espera de lectura.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CObject](../../mfc/reference/cobject-class.md) clase derivada de puntero que se debe convertir con seguridad correcto utilizando [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof).  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se llama la `CArchive` extracción ( ** >> **) operador sobrecargado para una [CObject](../../mfc/reference/cobject-class.md) puntero. **ReadObject**, a su vez, llama a la `Serialize` función de la clase archivada.  
  
 Si proporciona un distinto de cero `pClass` parámetro, que se obtiene mediante la [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) macro y, a continuación, la función comprueba la clase en tiempo de ejecución del objeto archivado. Se supone que ha usado el `IMPLEMENT_SERIAL` macro en la implementación de la clase.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CArchive::WriteObject](#writeobject).  
  
##  <a name="a-namereadstringa--carchivereadstring"></a><a name="readstring"></a>CArchive::ReadString  
 Llame a esta función miembro para leer los datos de texto en un búfer de archivo asociado a la `CArchive` objeto.  
  
```  
BOOL ReadString(CString& rString); 
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 `rString`  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contendrá la cadena resultante después de leerlo desde el archivo asociado al objeto CArchive.  
  
 `lpsz`  
 Especifica un puntero a un búfer proporcionado por el usuario que recibirá una cadena terminada en null de texto.  
  
 `nMax`  
 Especifica el número máximo de caracteres que se va a leer. Debe ser uno menor que el tamaño de la *lpsz* búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 En la versión que devuelve **BOOL**, **TRUE** si es correcto; **FALSE** en caso contrario.  
  
 En la versión que devuelve un `LPTSTR`, un puntero al búfer que contiene los datos de texto; **NULL** si se alcanzó el final del archivo.  
  
### <a name="remarks"></a>Comentarios  
 En la versión de la función miembro con el `nMax` parámetro, el búfer se almacenar hasta un límite de `nMax` - 1 caracteres. Lectura se detiene por un par de retorno de carro. Siempre se quitan los caracteres de nueva línea al final. En cualquier caso, se anexa un carácter nulo ('\0').  
  
 [CArchive::Read](#read) también está disponible para la entrada de modo de texto, pero no termina en un par de retorno de carro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CArchive::WriteString](#writestring).  
  
##  <a name="a-nameserializeclassa--carchiveserializeclass"></a><a name="serializeclass"></a>CArchive::SerializeClass  
 Llame a esta función miembro para almacenar y cargar la información de versión de una clase base.  
  
```  
void SerializeClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>Parámetros  
 `pClassRef`  
 Puntero a un objeto de clase en tiempo de ejecución de la clase base.  
  
### <a name="remarks"></a>Comentarios  
 `SerializeClass`lee o escribe la referencia a una clase para la `CArchive` objeto, según la dirección de la `CArchive`. Utilice `SerializeClass` en lugar de [ReadClass](#readclass) y [WriteClass](#writeclass) como una manera cómoda para serializar los objetos de clase base; `SerializeClass` requiere menos código y menos parámetros.  
  
 Como `ReadClass`, `SerializeClass` comprueba que la información de clase archivada es compatible con la clase en tiempo de ejecución. Si no es compatible, `SerializeClass` producirá un [CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Debe usar la clase en tiempo de ejecución [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); en caso contrario, `SerializeClass` producirá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Utilice la [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) macro para recuperar el valor de la `pRuntimeClass` parámetro. La clase base debe haber utilizado el [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#25;](../../mfc/codesnippet/cpp/carchive-class_17.h)]  
  
##  <a name="a-namesetloadparamsa--carchivesetloadparams"></a><a name="setloadparams"></a>CArchive::SetLoadParams  
 Llame a `SetLoadParams` cuando va a leer un gran número de `CObject`-objetos derivados de un archivo.  
  
```  
void SetLoadParams(UINT nGrowBy = 1024);
```  
  
### <a name="parameters"></a>Parámetros  
 `nGrowBy`  
 El número mínimo de ranuras de elemento para asignar si es necesario un aumento de tamaño.  
  
### <a name="remarks"></a>Comentarios  
 `CArchive`utiliza una matriz de carga para resolver las referencias a los objetos almacenados en el archivo. `SetLoadParams`permite establecer el tamaño al que crece la carga de matriz.  
  
 No se debe llamar a `SetLoadParams` después de cargar cualquier objeto o después de [MapObject](#mapobject) o [ReadObject](#readobject) se llama.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFCSerialization #](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="a-namesetobjectschemaa--carchivesetobjectschema"></a><a name="setobjectschema"></a>CArchive::SetObjectSchema  
 Llame a esta función miembro para establecer el esquema de objetos almacenado en el objeto de archivo a `nSchema`.  
  
```  
void SetObjectSchema(UINT nSchema);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSchema`  
 Especifica el esquema del objeto.  
  
### <a name="remarks"></a>Comentarios  
 La siguiente llamada a [GetObjectSchema](#getobjectschema) devolverá el valor almacenado en `nSchema`.  
  
 Utilice `SetObjectSchema` control de versiones avanzada; por ejemplo, cuando desee forzar a una versión concreta que se lean un `Serialize` función de una clase derivada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization Nº&27;](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]  
  
##  <a name="a-namesetstoreparamsa--carchivesetstoreparams"></a><a name="setstoreparams"></a>CArchive::SetStoreParams  
 Utilice `SetStoreParams` al almacenar una gran cantidad de `CObject`-derivado de objetos en un archivo.  
  
```  
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```  
  
### <a name="parameters"></a>Parámetros  
 *nHashSize*  
 Asigna el tamaño de la tabla hash para el puntero de interfaz. Debe ser un número primo.  
  
 `nBlockSize`  
 Especifica la granularidad de asignación de memoria para extender los parámetros. Debe ser una potencia de 2 para optimizar el rendimiento.  
  
### <a name="remarks"></a>Comentarios  
 `SetStoreParams`permite establecer el tamaño de la tabla hash y el tamaño del bloque de la asignación que se utiliza para identificar objetos únicos durante el proceso de serialización.  
  
 No se debe llamar a `SetStoreParams` después de que se almacenan todos los objetos, o después de [MapObject](#mapobject) o [WriteObject](#writeobject) se llama.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFCSerialization #](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="a-namewritea--carchivewrite"></a><a name="write"></a>CArchive:: Write  
 Escribe un número especificado de bytes en el archivo.  
  
```  
void Write(const void* lpBuf, INT nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuf`  
 Un puntero a un búfer proporcionado por el usuario que contiene los datos se escriban en el archivo.  
  
 `nMax`  
 Un entero que especifica el número de bytes que se escribirán en el archivo.  
  
### <a name="remarks"></a>Comentarios  
 El archivo no da formato a los bytes.  
  
 Puede usar el **escribir** función miembro dentro de su `Serialize` función escribir normal de las estructuras que están contenidos en los objetos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_MFCSerialization #](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]  
  
##  <a name="a-namewriteclassa--carchivewriteclass"></a><a name="writeclass"></a>CArchive::WriteClass  
 Use `WriteClass` para almacenar la información de versión y la clase de una clase base durante la serialización de la clase derivada.  
  
```  
void WriteClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>Parámetros  
 `pClassRef`  
 Un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura que corresponde a la referencia de la clase solicitada.  
  
### <a name="remarks"></a>Comentarios  
 `WriteClass`escribe una referencia a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) de la clase base para el `CArchive`. Utilice [CArchive::ReadClass](#readclass) para recuperar la referencia.  
  
 `WriteClass`comprueba que la información de clase archivada es compatible con la clase en tiempo de ejecución. Si no es compatible, `WriteClass` producirá un [CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Debe usar la clase en tiempo de ejecución [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); en caso contrario, `WriteClass` producirá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Puede usar [SerializeClass](#serializeclass) en lugar de `WriteClass`, que controla la lectura y escritura de la referencia de clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization&#28;](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]  
  
##  <a name="a-namewriteobjecta--carchivewriteobject"></a><a name="writeobject"></a>CArchive::WriteObject  
 Almacena especificado `CObject` al archivo.  
  
```  
void WriteObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>Parámetros  
 `pOb`  
 Puntero constante al objeto que se almacena.  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se llama la `CArchive` inserción ( ** << **) operador sobrecargado para `CObject`. **WriteObject**, a su vez, llama a la `Serialize` función de la clase archivada.  
  
 Debe utilizar el `IMPLEMENT_SERIAL` macro para habilitar el archivado. **WriteObject** escribe el nombre de clase de ASCII en el archivo. Este nombre de clase se valida posteriormente durante el proceso de carga. Un esquema de codificación especial evita la duplicación innecesaria de nombre de clase para varios objetos de la clase. Este esquema también evita el almacenamiento redundante de los objetos que son destinos de más de un puntero.  
  
 El objeto exacto encoding (método) (incluida la presencia del nombre de clase ASCII) es un detalle de implementación y podría cambiar en futuras versiones de la biblioteca.  
  
> [!NOTE]
>  Finalizar la creación, eliminación y actualización de todos los objetos antes de empezar a archivarlos. El archivo se dañará Si mezcla archivado con la modificación de objetos.  
  
### <a name="example"></a>Ejemplo  
 Para obtener una definición de la clase `CAge`, vea el ejemplo de [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).  
  
 [!code-cpp[NVC_MFCSerialization&#29;](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]  
  
##  <a name="a-namewritestringa--carchivewritestring"></a><a name="writestring"></a>CArchive::WriteString  
 Utilice esta función miembro para escribir datos de un búfer en el archivo asociado a la `CArchive` objeto.  
  
```  
void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpsz`  
 Especifica un puntero a un búfer que contiene una cadena de texto terminada en null.  
  
### <a name="remarks"></a>Comentarios  
 El carácter de terminación nulo ('\0') no se escribe en el archivo; tampoco es una nueva línea escribe automáticamente.  
  
 `WriteString`produce una excepción en respuesta a varias condiciones, incluidas la condición de disco lleno.  
  
 **Escribir** también está disponible, pero en lugar de terminar en un carácter null, escribe el número solicitado de bytes en el archivo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCSerialization Nº&30;](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CFile (clase)](../../mfc/reference/cfile-class.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [CSocket (clase)](../../mfc/reference/csocket-class.md)   
 [Clase CSocketFile](../../mfc/reference/csocketfile-class.md)

