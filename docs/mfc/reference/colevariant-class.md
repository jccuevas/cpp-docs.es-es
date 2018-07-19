---
title: Clase COleVariant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
dev_langs:
- C++
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41a93a89ed0ace158a0864d7987cafd838eed304
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853746"
---
# <a name="colevariant-class"></a>Clase COleVariant
Encapsula el [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) tipo de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleVariant::COleVariant](#colevariant)|Construye un objeto `COleVariant`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleVariant::Attach](#attach)|Adjunta una variante en una `COleVariant`.|  
|[COleVariant::ChangeType](#changetype)|Cambia el tipo de variante de este `COleVariant` objeto.|  
|[COleVariant::Clear](#clear)|Esto borra `COleVariant` objeto.|  
|[COleVariant::Detach](#detach)|Desasocia una variante de un `COleVariant` y devuelve la variante.|  
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Recupera una matriz de bytes de una matriz de variant existente.|  
|[COleVariant::SetString](#setstring)|Establece la cadena a un tipo determinado, normalmente ANSI.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Convierte un `COleVariant` valor en un `LPCVARIANT`.|  
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Convierte un `COleVariant` objeto en un `LPVARIANT`.|  
|[COleVariant::operator =](#operator_eq)|Copia un `COleVariant` valor.|  
|[COleVariant::operator ==](#operator_eq_eq)|Compara dos `COleVariant` valores.|  
|[COleVariant::operator &lt; &lt;, &gt;&gt;](#operator_lt_lt__gt_gt)|Salidas un `COleVariant` valor `CArchive` o `CDumpContext` y los introduce un `COleVariant` objeto `CArchive`.|  
  
## <a name="remarks"></a>Comentarios  
 Este tipo de datos se usa en la automatización OLE. En concreto, el [DISPPARAMS](http://msdn.microsoft.com/a16e5a21-766e-4287-b039-13429aa78f8b) estructura contiene un puntero a una matriz de estructuras VARIANT. Un `DISPPARAMS` estructura se usa para pasar parámetros al [IDispatch:: Invoke](http://msdn.microsoft.com/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
> [!NOTE]
>  Esta clase se deriva el `VARIANT` estructura. Esto significa que puede pasar un `COleVariant` en un parámetro que requiere un `VARIANT` y que los miembros de datos de la `VARIANT` estructura son miembros de datos accesibles de `COleVariant`.  
  
 Los dos relacionados con las clases MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) y [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) encapsular los tipos de datos variant moneda ( `VT_CY`) y la fecha ( `VT_DATE`). El `COleVariant` clase se usa habitualmente en las clases DAO; Vea estas clases para un uso típico de esta clase, por ejemplo [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [moneda](http://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e), [DISPPARAMS](http://msdn.microsoft.com/a16e5a21-766e-4287-b039-13429aa78f8b), y [IDispatch:: Invoke](http://msdn.microsoft.com/964ade8e-9d8a-4d32-bd47-aa678912a54d) entradas en el SDK de Windows.  
  
 Para obtener más información sobre la `COleVariant` clase y su uso en la automatización OLE, vea "Pasar parámetros de automatización OLE" en el artículo [automatización](../../mfc/automation.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tagVARIANT`  
  
 `COleVariant`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="attach"></a>  COleVariant::Attach  
 Llame a esta función para adjuntar el determinado [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) el objeto actual `COleVariant` objeto.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *varSrc*  
 Existente `VARIANT` objeto que se adjuntará a la actual `COleVariant` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función establece la [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) de *varSrc* en VT_EMPTY.  
  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) y [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) entradas en el SDK de Windows.  
  
##  <a name="colevariant"></a>  COleVariant::COleVariant  
 Construye un objeto `COleVariant`.  
  
```  
COleVariant(); 
COleVariant(const VARIANT& varSrc); 
COleVariant(const COleVariant& varSrc); 
COleVariant(LPCVARIANT pSrc); 
COleVariant(LPCTSTR lpszSrc); 
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc); 
COleVariant(CString& strSrc); 
COleVariant(BYTE nSrc); 
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2); 
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4); 
COleVariant(const COleCurrency& curSrc); 
COleVariant(float fltSrc); 
COleVariant(double dblSrc); 
COleVariant(const COleDateTime& timeSrc); 
COleVariant(const CByteArray& arrSrc); 
COleVariant(const CLongBinary& lbSrc); 
COleVariant(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parámetros  
 *varSrc*  
 Existente `COleVariant` o `VARIANT` objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 *pSrc*  
 Un puntero a un `VARIANT` objeto que se copiarán en el nuevo `COleVariant` objeto.  
  
 *lpszSrc*  
 Una cadena terminada en null que se copiará en el nuevo `COleVariant` objeto.  
  
 *vtSrc*  
 El `VARTYPE` para el nuevo `COleVariant` objeto.  
  
 *strSrc*  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 *nSrc*, *lSrc*  
 Un valor numérico que se va a copiar en el nuevo objeto `COleVariant`.  
  
 *vtSrc*  
 El `VARTYPE` para el nuevo `COleVariant` objeto.  
  
 *curSrc*  
 Un [COleCurrency](../../mfc/reference/colecurrency-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 *fltSrc*, *dblSrc*  
 Un valor numérico que se va a copiar en el nuevo objeto `COleVariant`.  
  
 *timeSrc*  
 Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 *arrSrc*  
 Un [CByteArray](../../mfc/reference/cbytearray-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 *lbSrc*  
 Un [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 *PIDL*  
 Un puntero a un [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) estructura que se copiará en el nuevo `COleVariant` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Todos estos constructores crean nuevos `COleVariant` objetos inicializados en el valor especificado. Una breve descripción de cada uno de estos constructores sigue.  
  
- **() COleVariant** crea vacío `COleVariant` objeto, VT_EMPTY.  
  
- **COleVariant (** *varSrc* **)** copia existente `VARIANT` o `COleVariant` objeto. El tipo variant se conserva.  
  
- **COleVariant (** `pSrc` **)** copia existente `VARIANT` o `COleVariant` objeto. El tipo variant se conserva.  
  
- **COleVariant (** `lpszSrc` **)** copia una cadena en el nuevo objeto, VT_BSTR (UNICODE).  
  
- **COleVariant (** `lpszSrc` **,** `vtSrc` **)** copia una cadena en el nuevo objeto. El parámetro *vtSrc* debe ser VT_BSTR (UNICODE) o VT_BSTRT (ANSI).  
  
- **COleVariant (** `strSrc` **)** copia una cadena en el nuevo objeto, VT_BSTR (UNICODE).  
  
- **COleVariant (** `nSrc` **)** copia un entero de 8 bits en el nuevo objeto, VT_UI1.  
  
- **COleVariant (** `nSrc` **,** `vtSrc` **)** copia en el nuevo objeto de un entero de 16 bits (o valor booleano). El parámetro *vtSrc* debe ser VT_I2 o VT_BOOL.  
  
- **COleVariant (** `lSrc` **,** `vtSrc` **)** copia en el nuevo objeto de un entero de 32 bits (o valor SCODE). El parámetro *vtSrc* debe ser VT_I4, VT_ERROR o VT_BOOL.  
  
- **COleVariant (** `curSrc` **)** copias un `COleCurrency` valor en el nuevo objeto, VT_CY.  
  
- **COleVariant (** `fltSrc` **)** copia un valor de punto flotante de 32 bits en el nuevo objeto, VT_R4.  
  
- **COleVariant (** `dblSrc` **)** copia un valor de punto flotante de 64 bits en el nuevo objeto, VT_R8.  
  
- **COleVariant (** `timeSrc` **)** copias un `COleDateTime` valor en el nuevo objeto, VT_DATE.  
  
- **COleVariant (** `arrSrc` **)** copias un `CByteArray` objeto en el nuevo objeto, VT_EMPTY.  
  
- **COleVariant (** `lbSrc` **)** copias un `CLongBinary` objeto en el nuevo objeto, VT_EMPTY.  
  
 Para obtener más información sobre SCODE, consulte [estructura de códigos de Error COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) en el SDK de Windows.  
  
##  <a name="changetype"></a>  COleVariant::ChangeType  
 Convierte el tipo de valor de variante de este `COleVariant` objeto.  
  
```  
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *VarType*  
 El [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) para este `COleVariant` objeto.  
  
 *pSrc*  
 Un puntero a la [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) objeto va a convertir. Si este valor es NULL, esto `COleVariant` objeto se usa como origen para la conversión.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4), y [VariantChangeType](http://msdn.microsoft.com/48a51e32-95d7-4eeb-8106-f5043ffa2fd1) entradas en el SDK de Windows.  
  
##  <a name="clear"></a>  COleVariant::Clear  
 Borra la `VARIANT`.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
 Esto establece el valor de VARTYPE para este objeto en VT_EMPTY. El `COleVariant` destructor llama a esta función.  
  
 Para obtener más información, consulte el `VARIANT`, VARTYPE, y `VariantClear` entradas en el SDK de Windows.  
  
##  <a name="detach"></a>  COleVariant::Detach  
 Desasocia subyacente [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) objeto desde este `COleVariant` objeto.  
  
```  
VARIANT Detach();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función establece la [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) para este `COleVariant` objeto en VT_EMPTY.  
  
> [!NOTE]
>  Después de llamar a `Detach`, es responsabilidad del llamador para llamar a `VariantClear` en resultante `VARIANT` estructura.  
  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4), y [VariantClear](http://msdn.microsoft.com/28741d81-8404-4f85-95d3-5c209ec13835) entradas en el SDK de Windows.  
  
##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray  
 Recupera una matriz de bytes de una matriz de variant existente  
  
```  
void GetByteArrayFromVariantArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Parámetros  
 *Bytes*  
 Una referencia a una existente [CByteArray](../../mfc/reference/cbytearray-class.md) objeto.  
  
##  <a name="operator_lpcvariant"></a>  COleVariant::operator LPCVARIANT  
 Este operador de conversión devuelve un `VARIANT` estructura cuyo valor se copia desde este `COleVariant` objeto.  
  
```  
operator LPCVARIANT() const; 
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="operator_lpvariant"></a>  COleVariant::operator LPVARIANT  
 Llamar a este operador de conversión para obtener acceso a subyacente `VARIANT` estructura para este `COleVariant` objeto.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  Cambia el valor en el `VARIANT` estructura accediendo el puntero devuelto por esta función cambiará el valor de esta `COleVariant` objeto.  
  
##  <a name="operator_eq"></a>  COleVariant::operator =  
 Estos operadores de asignaciones sobrecargados copian el valor de origen en este `COleVariant` objeto.  
  
```  
const COleVariant& operator=(const VARIANT& varSrc); 
const COleVariant& operator=(LPCVARIANT pSrc); 
const COleVariant& operator=(const COleVariant& varSrc); 
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc); 
const COleVariant& operator=(BYTE nSrc); 
const COleVariant& operator=(short nSrc); 
const COleVariant& operator=(long lSrc); 
const COleVariant& operator=(const COleCurrency& curSrc); 
const COleVariant& operator=(float fltSrc); 
const COleVariant& operator=(double dblSrc); 
const COleVariant& operator=(const COleDateTime& dateSrc); 
const COleVariant& operator=(const CByteArray& arrSrc); 
const COleVariant& operator=(const CLongBinary& lbSrc);
```  
  
### <a name="remarks"></a>Comentarios  
 A continuación se muestra una breve descripción de cada operador:  
  
- **operador = (** *varSrc ***)** copia una variante existente o `COleVariant` objeto en este objeto.  
  
- **operador = (** `pSrc` **)** copia el objeto de variante accediendo a *pSrc* en este objeto.  
  
- **operador = (** `lpszSrc` **)** copia una cadena terminada en null en este objeto y establece el valor de VARTYPE en VT_BSTR.  
  
- **operador = (** `strSrc` **)** copias un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto en este objeto y establece el valor de VARTYPE en VT_BSTR.  
  
- **operador = (** `nSrc` **)** copia un valor entero de 8 o 16 bits en este objeto. Si *nSrc* es un valor de 8 bits, el valor de VARTYPE esto está establecido en VT_UI1. Si *nSrc* es un valor de 16 bits y el valor de VARTYPE esto es VT_BOOL, mantenerse; de lo contrario, se establece en VT_I2.  
  
- **operador = (** `lSrc` **)** copia un valor entero de 32 bits en este objeto. Si el valor de VARTYPE esto es VT_ERROR, se mantienen; en caso contrario, se establece en VT_I4.  
  
- **operador = (** `curSrc` **)** copias un [COleCurrency](../../mfc/reference/colecurrency-class.md) objeto en este objeto y establece el valor de VARTYPE a VT_CY.  
  
- **operador = (** `fltSrc` **)** copia un valor de punto flotante de 32 bits en este objeto y establece el valor de VARTYPE en VT_R4.  
  
- **operador = (** `dblSrc` **)** copia un valor de punto flotante de 64 bits en este objeto y establece el valor de VARTYPE en VT_R8.  
  
- **operador = (** `dateSrc` **)** copias un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto en este objeto y establece el valor de VARTYPE a VT_DATE.  
  
- **operador = (** `arrSrc` **)** copias un [CByteArray](../../mfc/reference/cbytearray-class.md) objeto `COleVariant` objeto.  
  
- **operador = (** `lbSrc` **)** copias un [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto `COleVariant` objeto.  
  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) y [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) entradas en el SDK de Windows.  
  
##  <a name="operator_eq_eq"></a>  COleVariant::operator ==  
 Este operador compara dos valores variantes y devuelve cero si son iguales; en caso contrario, es 0.  
  
```  
BOOL operator==(const VARIANT& varSrc) const; 
BOOL operator==(LPCVARIANT pSrc) const;
```  
  
##  <a name="operator_lt_lt__gt_gt"></a>  COleVariant::operator &lt; &lt;, &gt;&gt;  
 Salidas un `COleVariant` valor `CArchive` o `CdumpContext` y los introduce un `COleVariant` objeto `CArchive`.  
  
```  
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,  
    OleVariant varSrc);
 
friend CArchive& AFXAPI operator<<(
    CArchive& ar,  
    COleVariant varSrc);
 
friend CArchive& AFXAPI operator>>(
    CArchive& ar,  
    COleVariant& varSrc);
```  
  
### <a name="remarks"></a>Comentarios  
 El `COleVariant` inserción ( **< \<**) admite el operador de volcado de diagnóstico y almacenar en un archivo. La extracción ( **>>**) operador puede cargar desde un archivo.  
  
##  <a name="setstring"></a>  COleVariant::SetString  
 Establece la cadena a un tipo determinado.  
  
```  
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszSrc*  
 Una cadena terminada en null que se copiará en el nuevo `COleVariant` objeto.  
  
 *vtSrc*  
 El valor de VARTYPE para el nuevo `COleVariant` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro *vtSrc* debe ser VT_BSTR (UNICODE) o VT_BSTRT (ANSI). `SetString` Normalmente se usa para establecer las cadenas a ANSI, desde el valor predeterminado para el [COleVariant::COleVariant](#colevariant) constructor con una cadena o el parámetro de puntero de cadena y no VARTYPE es UNICODE.  
  
 Un conjunto de registros en una compilación que no son UNICODE espera que las cadenas ANSI. Para DAO por lo tanto, las funciones que usan `COleVariant` objetos, si no va a crear un conjunto de registros UNICODE, debe usar el **COleVariant::COleVariant (** `lpszSrc` **,** `vtSrc` **)**  formulario del constructor con *vtSrc* establezca VT_BSTRT (ANSI) o use `SetString` con *vtSrc* establecido en VT_BSTRT para asegurarse de cadenas ANSI. Por ejemplo, el `CDaoRecordset` funciones [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) y [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) usar `COleVariant` objetos como parámetros. Estos objetos deben ser ANSI si el conjunto de registros DAO no es UNICODE.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



