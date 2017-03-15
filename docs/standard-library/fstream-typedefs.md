---
title: '&lt;fstream&gt; (Typedefs) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 4978b0b9f49fd0b0f4125c3dd2f17d07446bc6ac
ms.lasthandoff: 02/24/2017

---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; (Typedefs)
||||  
|-|-|-|  
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|  
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|  
|[wifstream](#wifstream)|[wofstream](#wofstream)|  
  
##  <a name="a-namefilebufa--filebuf"></a><a name="filebuf"></a>  filebuf  
 Un tipo `basic_filebuf` especializado en parámetros de plantilla `char`.  
  
```
typedef basic_filebuf<char, char_traits<char>> filebuf;
```  
  
### <a name="remarks"></a>Comentarios  
 Tipo sinónimo de la clase de plantilla [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.  
  
##  <a name="a-namefstreama--fstream"></a><a name="fstream"></a>  fstream  
 Un tipo `basic_fstream` especializado en parámetros de plantilla `char`.  
  
```
typedef basic_fstream<char, char_traits<char>> fstream;
```  
  
### <a name="remarks"></a>Comentarios  
 Tipo sinónimo de la clase de plantilla [basic_fstream](../standard-library/basic-fstream-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.  
  
##  <a name="a-nameifstreama--ifstream"></a><a name="ifstream"></a>  ifstream  
 Define una secuencia que se utilizará para leer datos de caracteres de byte único en serie desde un archivo. `ifstream`es un typedef que especializa la clase de plantilla `basic_ifstream` para `char`.  
  
 También está `wifstream`, un typedef que especializa `basic_ifstream` para leer caracteres de doble ancho `wchar_t`. Para obtener más información, vea [wifstream](../standard-library/fstream-typedefs.md#wifstream).  
  
```
typedef basic_ifstream<char, char_traits<char>> ifstream;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de la clase de plantilla `basic_ifstream`especializada en elementos del tipo char con rasgos de caracteres predeterminados. Un ejemplo es  
  
 `using namespace std;`  
  
 `ifstream infile("existingtextfile.txt");`  
  
 `if (!infile.bad())`  
  
 `{`  
  
 `// Dump the contents of the file to cout.`  
  
 `cout << infile.rdbuf();`  
  
 `infile.close();`  
  
 `}`  
  
##  <a name="a-nameofstreama--ofstream"></a><a name="ofstream"></a>  ofstream  
 Un tipo `basic_ofstream` especializado en parámetros de plantilla `char`.  
  
```
typedef basic_ofstream<char, char_traits<char>> ofstream;
```  
  
### <a name="remarks"></a>Comentarios  
 Tipo sinónimo de la clase de plantilla [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.  
  
##  <a name="a-namewfstreama--wfstream"></a><a name="wfstream"></a>  wfstream  
 Un tipo `basic_fstream` especializado en parámetros de plantilla `wchar_t`.  
  
```
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```  
  
### <a name="remarks"></a>Comentarios  
 Tipo sinónimo de la clase de plantilla [basic_fstream](../standard-library/basic-fstream-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.  
  
##  <a name="a-namewifstreama--wifstream"></a><a name="wifstream"></a>  wifstream  
 Un tipo `basic_ifstream` especializado en parámetros de plantilla `wchar_t`.  
  
```
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```  
  
### <a name="remarks"></a>Comentarios  
 Tipo sinónimo de la clase de plantilla [basic_ifstream](../standard-library/basic-ifstream-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.  
  
##  <a name="a-namewofstreama--wofstream"></a><a name="wofstream"></a>  wofstream  
 Un tipo `basic_ofstream` especializado en parámetros de plantilla `wchar_t`.  
  
```
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```  
  
### <a name="remarks"></a>Comentarios  
 Tipo sinónimo de la clase de plantilla [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.  
  
##  <a name="a-namewfilebufa--wfilebuf"></a><a name="wfilebuf"></a>  wfilebuf  
 Un tipo `basic_filebuf` especializado en parámetros de plantilla `wchar_t`.  
  
```
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```  
  
### <a name="remarks"></a>Comentarios  
 Tipo sinónimo de la clase de plantilla [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.  
  
## <a name="see-also"></a>Vea también  
 [\<fstream>](../standard-library/fstream.md)




