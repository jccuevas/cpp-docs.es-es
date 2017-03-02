---
title: Clase COleSafeArray | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleSafeArray
dev_langs:
- C++
helpviewer_keywords:
- COleSafeArray class
- arrays [C++], safe
- safe arrays
- ODBC, safe arrays
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
caps.latest.revision: 22
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
ms.openlocfilehash: 3cb6fa49e3adf7e14c34baf7feb64d12e54f2758
ms.lasthandoff: 02/24/2017

---
# <a name="colesafearray-class"></a>Clase COleSafeArray
Una clase para trabajar con matrices de tipo y dimensión arbitrarios.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleSafeArray : public tagVARIANT  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleSafeArray::COleSafeArray](#colesafearray)|Construye un objeto `COleSafeArray`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleSafeArray::AccessData](#accessdata)|Recupera un puntero a los datos de la matriz.|  
|[COleSafeArray::AllocData](#allocdata)|Asigna memoria para la matriz.|  
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Asigna memoria para el descriptor de la matriz segura.|  
|[COleSafeArray::Attach](#attach)|Proporciona control de existente **VARIANT** de matriz a la `COleSafeArray` objeto.|  
|[COleSafeArray::Clear](#clear)|Libera todos los datos de la base de **VARIANT**.|  
|[COleSafeArray::Copy](#copy)|Crea una copia de una matriz existente.|  
|[COleSafeArray::Create](#create)|Crea una matriz segura.|  
|[COleSafeArray::CreateOneDim](#createonedim)|Crea un unidimensional `COleSafeArray` objeto.|  
|[COleSafeArray::Destroy](#destroy)|Destruye una matriz existente.|  
|[COleSafeArray::DestroyData](#destroydata)|Destruye los datos en una matriz segura.|  
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Destruye un descriptor de la matriz segura.|  
|[COleSafeArray::Detach](#detach)|Desasocia el **VARIANT** matriz desde el `COleSafeArray` de objeto (de modo que no se liberarán los datos).|  
|[COleSafeArray::GetByteArray](#getbytearray)|Copia el contenido de la matriz segura en una [CByteArray](../../mfc/reference/cbytearray-class.md).|  
|[COleSafeArray::GetDim](#getdim)|Devuelve el número de dimensiones de la matriz.|  
|[COleSafeArray::GetElement](#getelement)|Recupera un único elemento de la matriz segura.|  
|[COleSafeArray::GetElemSize](#getelemsize)|Devuelve el tamaño, en bytes, de un elemento en una matriz segura.|  
|[COleSafeArray::GetLBound](#getlbound)|Devuelve el límite inferior de cualquier dimensión de la matriz segura.|  
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Devuelve el número de elementos de unidimensional `COleSafeArray` objeto.|  
|[COleSafeArray::GetUBound](#getubound)|Devuelve el límite superior de cualquier dimensión de la matriz segura.|  
|[COleSafeArray::Lock](#lock)|Incrementa el recuento de bloqueos de una matriz y coloca un puntero a los datos de la matriz en el descriptor de la matriz.|  
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Devuelve un puntero al elemento indizado.|  
|[COleSafeArray::PutElement](#putelement)|Asigna un único elemento en la matriz.|  
|[COleSafeArray::Redim](#redim)|Cambia el límite menos significativo (derecho) de la matriz segura.|  
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Cambia el número de elementos de un unidimensional `COleSafeArray` objeto.|  
|[COleSafeArray::UnaccessData](#unaccessdata)|Reduce el bloqueo del contador de una matriz e invalida el puntero recuperado por `AccessData`.|  
|[COleSafeArray::Unlock](#unlock)|Reduce el recuento de bloqueos de una matriz por lo que se puede liberar o cambiar de tamaño.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Tiene acceso a la base de **VARIANT** estructura de la `COleSafeArray` objeto.|  
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Tiene acceso a la base de **VARIANT** estructura de la `COleSafeArray` objeto.|  
|[COleSafeArray::operator =](#operator_eq)|Copia los valores en una `COleSafeArray` objeto ( **SAFEARRAY**, **VARIANT**, `COleVariant`, o `COleSafeArray` matriz).|  
|[COleSafeArray::operator ==](#operator_eq_eq)|Compara dos matrices variant ( **SAFEARRAY**, **variante**, `COleVariant`, o `COleSafeArray` matrices).|  
|[COleSafeArray::operator&lt;&lt;](#operator_lt_lt)|Envía el contenido de una `COleSafeArray` objeto en el contexto de volcado.|  
  
## <a name="remarks"></a>Comentarios  
 `COleSafeArray`se deriva de OLE **VARIANT** estructura. OLE **SAFEARRAY** están disponibles a través de funciones miembro `COleSafeArray`, así como un conjunto de funciones miembro diseñado específicamente para las matrices unidimensionales de bytes.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tagVARIANT`  
  
 `COleSafeArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="a-nameaccessdataa--colesafearrayaccessdata"></a><a name="accessdata"></a>COleSafeArray::AccessData  
 Recupera un puntero a los datos de la matriz.  
  
```  
void AccessData(void** ppvData);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppvData`  
 Un puntero a un puntero a los datos de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFCOleContainer #](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]  
  
##  <a name="a-nameallocdataa--colesafearrayallocdata"></a><a name="allocdata"></a>COleSafeArray::AllocData  
 Asigna memoria para una matriz segura.  
  
```  
void AllocData();
```  
  
### <a name="remarks"></a>Comentarios  
 En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="a-nameallocdescriptora--colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a>COleSafeArray::AllocDescriptor  
 Asigna memoria para el descriptor de la matriz segura.  
  
```  
void AllocDescriptor(DWORD dwDims);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDims`  
 Número de dimensiones de la matriz segura.  
  
### <a name="remarks"></a>Comentarios  
 En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="a-nameattacha--colesafearrayattach"></a><a name="attach"></a>COleSafeArray::Attach  
 Proporciona control de los datos en un **VARIANT** de matriz a la `COleSafeArray` objeto.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *varSrc*  
 Un **VARIANT** objeto. El *varSrc* parámetro debe tener la [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)**VT_ARRAY**.  
  
### <a name="remarks"></a>Comentarios  
 El origen de **VARIANT**del tipo está establecido en `VT_EMPTY`. Esta función borra los datos de la matriz actual, si existe.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="a-namecleara--colesafearrayclear"></a><a name="clear"></a>COleSafeArray::Clear  
 Borra la matriz segura.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
 La función borra una matriz segura estableciendo el `VARTYPE` del objeto para `VT_EMPTY`. El contenido actual se libera y se libera la matriz.  
  
##  <a name="a-namecolesafearraya--colesafearraycolesafearray"></a><a name="colesafearray"></a>COleSafeArray::COleSafeArray  
 Construye un objeto `COleSafeArray`.  
  
```  
COleSafeArray();

 
COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

 
COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);  
  
COleSafeArray(const COleSafeArray& saSrc);  
COleSafeArray(const VARIANT& varSrc);  
  COleSafeArray(LPCVARIANT pSrc);  
COleSafeArray(const COleVariant& varSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `saSrc`  
 Existente `COleSafeArray` objeto o **SAFEARRAY** que se copiará en el nuevo `COleSafeArray` objeto.  
  
 `vtSrc`  
 El **VARTYPE** del nuevo `COleSafeArray` objeto.  
  
 `psaSrc`  
 Un puntero a un **SAFEARRAY** que se copiará en el nuevo `COleSafeArray` objeto.  
  
 *varSrc*  
 Existente **VARIANT** o `COleVariant` objeto que se copiará en el nuevo `COleSafeArray` objeto.  
  
 `pSrc`  
 Un puntero a un **VARIANT** objeto que se copiará en el nuevo `COleSafeArray` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Todos estos constructores crean nuevos `COleSafeArray` objetos. Si no hay ningún parámetro, una cadena vacía `COleSafeArray` se crea el objeto ( `VT_EMPTY`). Si el `COleSafeArray` se copia de otra matriz cuya [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) se conoce de forma implícita (un `COleSafeArray`, `COleVariant`, o **VARIANT**), el **VARTYPE** del origen de la matriz se conserva y no es necesario especificar. Si el `COleSafeArray` se copia de otra matriz cuya **VARTYPE** no se conoce ( **SAFEARRAY**), el **VARTYPE** debe especificarse en el `vtSrc` parámetro.  
  
 En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="a-namecopya--colesafearraycopy"></a><a name="copy"></a>COleSafeArray::Copy  
 Crea una copia de una matriz segura existente.  
  
```  
void Copy(LPSAFEARRAY* ppsa);
```  
  
### <a name="parameters"></a>Parámetros  
 *ppsa*  
 Puntero a una ubicación en la que se va a devolver el nuevo descriptor de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="a-namecreatea--colesafearraycreate"></a><a name="create"></a>COleSafeArray::Create  
 Asigna e inicializa los datos de la matriz.  
  
```  
void Create(
    VARTYPE vtSrc,  
    DWORD dwDims,  
    DWORD* rgElements);

 
void Create(
    VARTYPE vtSrc,  
    DWORD dwDims,  
    SAFEARRAYBOUND* rgsabounds);
```  
  
### <a name="parameters"></a>Parámetros  
 `vtSrc`  
 El tipo base de la matriz (es decir, el **VARTYPE** de cada elemento de la matriz). El **VARTYPE** está restringida a un subconjunto de los tipos variant. Ni el **VT_ARRAY** ni **VT_BYREF** se puede establecer la marca. `VT_EMPTY`y **VT_NULL** no son tipos base válidos para la matriz. Todos los demás tipos son válidos.  
  
 `dwDims`  
 Número de dimensiones de la matriz. Esto se puede cambiar después de crea la matriz con [Redim](#redim).  
  
 *rgElements*  
 Puntero a una matriz del número de elementos para cada dimensión de la matriz.  
  
 *rgsabounds*  
 Puntero a un vector de límites (uno para cada dimensión) para asignar la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Esta función borrará los datos de la matriz actual si es necesario. En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº&27;](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="a-namecreateonedima--colesafearraycreateonedim"></a><a name="createonedim"></a>COleSafeArray::CreateOneDim  
 Crea un nuevo unidimensional `COleSafeArray` objeto.  
  
```  
void CreateOneDim(
    VARTYPE vtSrc,  
    DWORD dwElements,  
    const void* pvSrcData = NULL,  
    long nLBound = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `vtSrc`  
 El tipo base de la matriz (es decir, el **VARTYPE** de cada elemento de la matriz).  
  
 `dwElements`  
 Número de elementos de la matriz. Esto se puede cambiar después de crea la matriz con [ResizeOneDim](#resizeonedim).  
  
 `pvSrcData`  
 Puntero a los datos que se va a copiar en la matriz.  
  
 *nLBound*  
 El límite inferior de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 La función asigna e inicializa los datos de la matriz, copiando los datos especificados, si el puntero `pvSrcData` no **NULL**.  
  
 En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#28;](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]  
  
##  <a name="a-namedestroya--colesafearraydestroy"></a><a name="destroy"></a>COleSafeArray::Destroy  
 Destruye un descriptor de matriz existente y todos los datos de la matriz.  
  
```  
void Destroy();
```  
  
### <a name="remarks"></a>Comentarios  
 Si los objetos se almacenan en la matriz, se libera de cada objeto. En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="a-namedestroydataa--colesafearraydestroydata"></a><a name="destroydata"></a>COleSafeArray::DestroyData  
 Destruye todos los datos en una matriz segura.  
  
```  
void DestroyData();
```  
  
### <a name="remarks"></a>Comentarios  
 Si los objetos se almacenan en la matriz, se libera de cada objeto. En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="a-namedestroydescriptora--colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a>COleSafeArray::DestroyDescriptor  
 Destruye un descriptor de la matriz segura.  
  
```  
void DestroyDescriptor();
```  
  
### <a name="remarks"></a>Comentarios  
 En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="a-namedetacha--colesafearraydetach"></a><a name="detach"></a>COleSafeArray::Detach  
 Desasocia el **VARIANT** datos desde el `COleSafeArray` objeto.  
  
```  
VARIANT Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Subyacente **VARIANT** valor en el `COleSafeArray` objeto.  
  
### <a name="remarks"></a>Comentarios  
 La función separa los datos en una matriz segura estableciendo el [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) del objeto para `VT_EMPTY`. Es responsabilidad del llamador liberar la matriz mediante una llamada a la función de Windows [VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835).  
  
 En caso de error, la función produce una [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleSafeArray::PutElement](#putelement).  
  
##  <a name="a-namegetbytearraya--colesafearraygetbytearray"></a><a name="getbytearray"></a>COleSafeArray::GetByteArray  
 Copia el contenido de la matriz segura en un `CByteArray`.  
  
```  
void GetByteArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Parámetros  
 `bytes`  
 Una referencia a un [CByteArray](../../mfc/reference/cbytearray-class.md) objeto.  
  
##  <a name="a-namegetdima--colesafearraygetdim"></a><a name="getdim"></a>COleSafeArray::GetDim  
 Devuelve el número de dimensiones de la `COleSafeArray` objeto.  
  
```  
DWORD GetDim();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de dimensiones de la matriz segura.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº&27;](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="a-namegetelementa--colesafearraygetelement"></a><a name="getelement"></a>COleSafeArray::GetElement  
 Recupera un único elemento de la matriz segura.  
  
```  
void GetElement(
    long* rgIndices,  
    void* pvData);
```  
  
### <a name="parameters"></a>Parámetros  
 `rgIndices`  
 Puntero a una matriz de índices para cada dimensión de la matriz.  
  
 `pvData`  
 Puntero a la ubicación para colocar el elemento de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Esta función llama automáticamente a las funciones de windows `SafeArrayLock` y `SafeArrayUnlock` antes y después de recuperar el elemento. Si el elemento de datos es una cadena, un objeto o una variante, la función copia el elemento de la forma correcta. El parámetro `pvData` debe apuntar a una gran suficiente búfer para que contenga el elemento.  
  
 En caso de error, la función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#29;](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]  
  
##  <a name="a-namegetelemsizea--colesafearraygetelemsize"></a><a name="getelemsize"></a>COleSafeArray::GetElemSize  
 Recupera el tamaño de un elemento en un `COleSafeArray` objeto.  
  
```  
DWORD GetElemSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño, en bytes, de los elementos de la matriz segura.  
  
##  <a name="a-namegetlbounda--colesafearraygetlbound"></a><a name="getlbound"></a>COleSafeArray::GetLBound  
 Devuelve el límite inferior de cualquier dimensión de un `COleSafeArray` objeto.  
  
```  
void GetLBound(
    DWORD dwDim,  
    long* pLBound);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDim`  
 La dimensión de matriz para el que se va a obtener el límite inferior.  
  
 *pLBound*  
 Puntero a la ubicación para devolver el límite inferior.  
  
### <a name="remarks"></a>Comentarios  
 En caso de error, la función produce una [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº&30;](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]  
  
##  <a name="a-namegetonedimsizea--colesafearraygetonedimsize"></a><a name="getonedimsize"></a>COleSafeArray::GetOneDimSize  
 Devuelve el número de elementos de unidimensional `COleSafeArray` objeto.  
  
```  
DWORD GetOneDimSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de la matriz unidimensional de seguro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="a-namegetubounda--colesafearraygetubound"></a><a name="getubound"></a>COleSafeArray::GetUBound  
 Devuelve el límite superior de cualquier dimensión de la matriz segura.  
  
```  
void GetUBound(
    DWORD dwDim,  
    long* pUBound);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDim`  
 La dimensión de matriz para el que se va a obtener el límite superior.  
  
 *pUBound*  
 Puntero a la ubicación para devolver el límite superior.  
  
### <a name="remarks"></a>Comentarios  
 En caso de error, la función produce una [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#31;](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]  
  
##  <a name="a-namelocka--colesafearraylock"></a><a name="lock"></a>COleSafeArray::Lock  
 Incrementa el recuento de bloqueos de una matriz y el lugar de un puntero a los datos de la matriz en el descriptor de la matriz.  
  
```  
void Lock();
```  
  
### <a name="remarks"></a>Comentarios  
 En caso de error, produce una [COleException](../../mfc/reference/coleexception-class.md).  
  
 Es válido hasta que el puntero en el descriptor de la matriz `Unlock` se llama. Las llamadas a `Lock` pueden anidarse; un número igual de llamadas a `Unlock` son necesarios.  
  
 No se puede eliminar una matriz mientras está bloqueado.  
  
##  <a name="a-nameoperatorlpcvarianta--colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleSafeArray::operator LPCVARIANT  
 Llame a este operador de conversión para tener acceso a la base de **VARIANT** estructura de este `COleSafeArray` objeto.  
  
```  
operator LPCVARIANT() const;  
```  
  
##  <a name="a-nameoperatorlpvarianta--colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleSafeArray::operator LPVARIANT  
 Llame a este operador de conversión para tener acceso a la base de **VARIANT** estructura de este `COleSafeArray` objeto.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que al cambiar el valor de la **VARIANT** estructura accediendo el puntero devuelto por esta función cambiará el valor de esta `COleSafeArray` objeto.  
  
##  <a name="a-nameoperatoreqa--colesafearrayoperator-"></a><a name="operator_eq"></a>COleSafeArray::operator =  
 Estos operadores de asignaciones sobrecargados copiar el valor de origen en esta `COleSafeArray` objeto.  
  
```  
COleSafeArray& operator=(const COleSafeArray& saSrc);  
COleSafeArray& operator=(const VARIANT& varSrc);  
  COleSafeArray& operator=(LPCVARIANT pSrc);  
COleSafeArray& operator=(const COleVariant& varSrc);
```  
  
### <a name="remarks"></a>Comentarios  
 A continuación se muestra una breve descripción de cada operador:  
  
- **operador = (** *saSrc* **)** copia existente `COleSafeArray` objeto en este objeto.  
  
- **operador = (** *varSrc***)** copia existente **VARIANT** o `COleVariant` matriz en este objeto.  
  
- **operador = (** `pSrc` **)** copias del **VARIANT** objeto de matriz de acceso `pSrc` en este objeto.  
  
##  <a name="a-nameoperatoreqeqa--colesafearrayoperator-"></a><a name="operator_eq_eq"></a>COleSafeArray::operator ==  
 Este operador compara dos matrices ( **SAFEARRAY**, **VARIANT**, `COleVariant`, o `COleSafeArray` matrices) y devuelve distinto de cero si son iguales; de lo contrario, 0.  
  
```  
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;  
   
BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;  
   
BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;  ```  
  
### Remarks  
 Two arrays are equal if they have an equal number of dimensions, equal size in each dimension, and equal element values.  
  
##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;  
 The `COleSafeArray` insertion (<<) operator supports diagnostic dumping and storing of a `COleSafeArray` object to an archive.  
  
```  
Operador CDumpContext AFXAPI de aspecto<( CDumpContext& dc, cdumpcontext&=""></( CDumpContext& dc,>  
    COleSafeArray aspecto saSrc);
```  
  
##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex  
 Returns a pointer to the element specified by the index values.  
  
```  
void PtrOfIndex (long* rgIndices, void** ppvData);
```  
  
### Parameters  
 `rgIndices`  
 An array of index values that identify an element of the array. All indexes for the element must be specified.  
  
 `ppvData`  
 On return, pointer to the element identified by the values in `rgIndices`.  
  
##  <a name="putelement"></a>  COleSafeArray::PutElement  
 Assigns a single element into the array.  
  
```  
void PutElement (long* rgIndices, void* pvData);
```  
  
### Parameters  
 `rgIndices`  
 Pointer to an array of indexes for each dimension of the array.  
  
 `pvData`  
 Pointer to the data to assign to the array. **VT_DISPATCH**, **VT_UNKNOWN**, and `VT_BSTR` variant types are pointers and do not require another level of indirection.  
  
### Remarks  
 This function automatically calls the Windows functions [SafeArrayLock](https://msdn.microsoft.com/library/windows/desktop/ms221492.aspx) and [SafeArrayUnlock](https://msdn.microsoft.com/library/windows/desktop/ms221246.aspx) before and after assigning the element. If the data element is a string, object, or variant, the function copies it correctly, and if the existing element is a string, object, or variant, it is cleared correctly.  
  
 Note that you can have multiple locks on an array, so you can put elements into an array while the array is locked by other operations.  
  
 On error, the function throws a [CMemoryException](../../mfc/reference/cmemoryexception-class.md) or [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
 [!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]  
  
##  <a name="redim"></a>  COleSafeArray::Redim  
 Changes the least significant (rightmost) bound of a safe array.  
  
```  
void Redim (SAFEARRAYBOUND * psaboundNew);
```  
  
### Parameters  
 *psaboundNew*  
 Pointer to a new safe array bound structure containing the new array bound. Only the least significant dimension of an array may be changed.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim  
 Changes the number of elements in a one-dimensional `COleSafeArray` object.  
  
```  
void ResizeOneDim (DWORD dwElements);
```  
  
### Parameters  
 `dwElements`  
 Number of elements in the one-dimensional safe array.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData  
 Decrements the lock count of an array and invalidates the pointer retrieved by `AccessData`.  
  
```  
void UnaccessData();
```  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="unlock"></a>  COleSafeArray::Unlock  
 Decrements the lock count of an array so it can be freed or resized.  
  
```  
void Unlock();
```  
  
### Remarks  
 This function is called after access to the data in an array is finished. On error, it throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)

