---
title: Clase CRecentFileList | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRecentFileList
dev_langs:
- C++
helpviewer_keywords:
- files [C++], most recently used
- MRU files
- CRecentFileList class
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
caps.latest.revision: 19
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
ms.openlocfilehash: 5d18daee2e4d809c750ae4654d731888df1db39e
ms.lasthandoff: 02/24/2017

---
# <a name="crecentfilelist-class"></a>Clase CRecentFileList
Admite el control de lista de los archivos utilizados más recientemente (MRU).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRecentFileList  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRecentFileList::CRecentFileList](#crecentfilelist)|Construye un objeto `CRecentFileList`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRecentFileList::Add](#add)|Agrega un archivo a la lista de archivos utilizados más Recientemente.|  
|[CRecentFileList::GetDisplayName](#getdisplayname)|Proporciona un nombre para mostrar del menú de un nombre de archivo utilizados más Recientemente.|  
|[CRecentFileList::GetSize](#getsize)|Recupera el número de archivos en la lista de archivos utilizados más Recientemente.|  
|[CRecentFileList::ReadList](#readlist)|Lee la lista de archivos utilizados más Recientemente en el registro o. Archivo INI.|  
|[CRecentFileList::Remove](#remove)|Quita un archivo de la lista de archivos utilizados más Recientemente.|  
|[CRecentFileList::UpdateMenu](#updatemenu)|Actualiza la presentación de menús de la lista de archivos utilizados más Recientemente.|  
|[CRecentFileList::WriteList](#writelist)|Escribe la lista de archivos utilizados más Recientemente desde el registro o. Archivo INI.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[[] CRecentFileList::operator](#operator_at)|Devuelve un `CString` objeto en una posición determinada.|  
  
## <a name="remarks"></a>Comentarios  
 Los archivos se pueden sumar o eliminan de la lista de archivos utilizados más Recientemente, la lista de archivos se puede leer o escribir en el registro o una. Pueden actualizar el archivo INI y el menú Mostrar la lista de archivos utilizados más Recientemente.  
  
 Para obtener más información acerca de los elementos de menú utilizados más Recientemente, consulte  
  
-   Artículo de Knowledge Base Q243751: HOWTO: agregar controladores de comandos para elementos de menú utilizados más Recientemente en la aplicación MFC  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CRecentFileList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxadv.h  
  
##  <a name="a-nameadda--crecentfilelistadd"></a><a name="add"></a>CRecentFileList::Add  
 Agrega un archivo a la lista de archivos usa más recientemente (MRU).  
  
```  
virtual void Add(LPCTSTR lpszPathName);

 
virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

 
void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

 
void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

 
void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Especifica la ruta de acceso para agregarse a la lista.  
  
 `lpszAppID`  
 Especifica el identificador de modelo de usuario de aplicación para la aplicación.  
  
 `pItem`  
 Especifica un puntero al elemento de Shell para agregarse a la lista.  
  
 `pLink`  
 Especifica un puntero al vínculo del Shell para agregarse a la lista.  
  
 `pidl`  
 Especifica al LISTA_ID para el elemento de shell que debe agregarse a la carpeta documentos recientes.  
  
### <a name="remarks"></a>Comentarios  
 El nombre de archivo se agregará a la parte superior de la lista de elementos utilizados Recientemente. Si el nombre de archivo ya existe en la lista de elementos utilizados Recientemente, se desplazará a la parte superior.  
  
##  <a name="a-namecrecentfilelista--crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a>CRecentFileList::CRecentFileList  
 Construye un objeto `CRecentFileList`.  
  
```  
CRecentFileList(
    UINT nStart,  
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntryFormat,  
    int nSize,  
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStart`  
 Desplazamiento de la numeración en la pantalla de menú de la lista de archivos MRU (usado más recientemente).  
  
 `lpszSection`  
 Apunta al nombre de la sección del registro o de la aplicación. Archivo INI donde es leer o escribir la lista de archivos utilizados más Recientemente.  
  
 `lpszEntryFormat`  
 Apunta a una cadena de formato que se utilizará para los nombres de las entradas almacenadas en el registro o la aplicación. Archivo INI.  
  
 `nSize`  
 Número máximo de archivos en la lista de archivos utilizados más Recientemente.  
  
 `nMaxDispLen`  
 Longitud máxima, en caracteres, para la presentación de menú de un nombre de archivo en la lista de archivos utilizados más Recientemente.  
  
### <a name="remarks"></a>Comentarios  
 La cadena de formato que apunta `lpszEntryFormat` debe contener "%d", que se utilizará para sustituir el índice de cada elemento de utilizados más Recientemente. Por ejemplo, si la cadena de formato es `"file%d"` , a continuación, las entradas se denominará `file0`, `file1`, y así sucesivamente.  
  
##  <a name="a-namegetdisplaynamea--crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a>CRecentFileList::GetDisplayName  
 Obtiene un nombre para mostrar de un archivo en la lista de archivos utilizados más Recientemente, para su uso en la pantalla de menú de la lista de elementos utilizados Recientemente.  
  
```  
virtual BOOL GetDisplayName(
    CString& strName,  
    int nIndex,  
    LPCTSTR lpszCurDir,  
    int nCurDir,  
    BOOL bAtLeastName = TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `strName`  
 Ruta de acceso completa del archivo cuyo nombre se mostrará en la lista del menú de archivos utilizados más Recientemente.  
  
 `nIndex`  
 Índice de base cero del archivo en la lista de archivos utilizados más Recientemente.  
  
 *lpszCurDir*  
 Cadena que contiene el directorio actual.  
  
 *nCurDir*  
 Longitud de la cadena del directorio actual.  
  
 `bAtLeastName`  
 Si es distinto de cero, indica que se debe devolver el nombre base del archivo, incluso si supera la longitud máxima de visualización (pasado como el `nMaxDispLen` parámetro para el `CRecentFileList` constructor).  
  
### <a name="return-value"></a>Valor devuelto  
 **FALSE** si no hay ningún nombre de archivo en el índice especificado en la lista de archivos usa más recientemente (MRU).  
  
### <a name="remarks"></a>Comentarios  
 Si el archivo está en el directorio actual, la función deja el directorio de la presentación. Si el nombre de archivo es demasiado largo, se eliminan el directorio y la extensión. Si el nombre de archivo sigue siendo demasiado largo, el nombre para mostrar se establece en una cadena vacía a menos que `bAtLeastName` es distinto de cero.  
  
##  <a name="a-namegetsizea--crecentfilelistgetsize"></a><a name="getsize"></a>CRecentFileList::GetSize  
 Recupera el número de archivos en la lista de archivos utilizados más Recientemente.  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de archivos actual más archivos usados recientemente (MRU).  
  
##  <a name="a-nameoperatorata--crecentfilelistoperator--"></a><a name="operator_at"></a>[] CRecentFileList::operator  
 El subíndice sobrecargado ( `[]`) operador devuelve un único `CString` especificado por el índice de base cero en `nIndex`.  
  
```  
CString& operator[ ](int nindex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero de un `CString` en un conjunto de `CString`s.  
  
##  <a name="a-namereadlista--crecentfilelistreadlist"></a><a name="readlist"></a>CRecentFileList::ReadList  
 Lee la mayoría de la archivos usados recientemente (MRU) desde el registro o la aplicación. Archivo INI.  
  
```  
virtual void ReadList();
```  
  
##  <a name="a-nameremovea--crecentfilelistremove"></a><a name="remove"></a>CRecentFileList::Remove  
 Quita un archivo de la lista de archivos utilizados más Recientemente.  
  
```  
virtual void Remove(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero del archivo que se va a quitar de la lista de archivos usa más recientemente (MRU).  
  
##  <a name="a-nameupdatemenua--crecentfilelistupdatemenu"></a><a name="updatemenu"></a>CRecentFileList::UpdateMenu  
 Actualiza la presentación de menús de la lista de archivos utilizados más Recientemente.  
  
```  
virtual void UpdateMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a la [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto para el menú de lista de archivos de utilizados más recientemente (MRU).  
  
##  <a name="a-namewritelista--crecentfilelistwritelist"></a><a name="writelist"></a>CRecentFileList::WriteList  
 Escribe la mayoría de la archivos usados recientemente (MRU) en el registro o la aplicación. Archivo INI.  
  
```  
virtual void WriteList();
```  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




