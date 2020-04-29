# rep2_ip2host

rep2(open774��)�Ŗ��O����IP�A�h���X������΋t���������ăz�X�g���ɏ�����������́B  
�񓯊��Ńz�X�g���̋t���������ď���������̂ŃX�����\������Ă��珑���ς��܂Ń��O������܂��B  
HTML5��Web Storage���g���ău���E�U���ɋt�������ʂ��L���b�V��������悤�ɂ��Ă���̂�2��ڈȍ~�L���b�V���ɂ���Ώ��������ł��B  
Web Storage�Ή��̃u���E�U�łȂ��ꍇ��rep2�T�[�o�[��/p2-php/data/tmp/�ɃL���b�V���t�@�C�������܂��B  
�܂��A�t���������z�X�g����rep2�̖��O���̂��ځ[�񏈗��������ĊY������Γ������ځ[�񂵂܂��B  
�t������rep2�T�[�o�[���ōs���A���������̓u���E�U����jQuery�œ��I�ɍs���Ă��邽��html�\�[�X�ɂ͔��f����܂���B

## Install
  * lib/ip2host.inc.php  
  * rep2/ip2host.php
 
�����ꂼ��̊���/p2-php�̒��ɓ���Ă��������B  
���̌�A  
  * lib/read_footer.inc.php (PC�p)
  * lib/read_footer_i.inc.php (�X�}�z�p)

�̍Ō���̕����ɁA
```php
// ��������
require P2_LIB_DIR . '/ip2host.inc.php';
// �����܂�

// ====
echo '</body></html>';
```
��ǋL���Ă��������B

## Environment
Linux(CentOS)��PHP7+Apache�œ���m�F���Ă��܂��B

## Note
### Cache
�L���b�V����HTML5��Web Storage(sessionStorage)���g�p���Ă��܂��B  
���̂��ߕʃ^�u�A�u���E�U�̍ċN���ȂǂŃL���b�V���͏����܂��B  
localStorage���g�p�ł��A�L���b�V�����u���E�U���ɔ��i�v�I�ɕێ�����ꍇ��ip2host.inc.php��
```JavaScript
st = sessionStorage;
//  LocalStorage���g���ꍇ�͉��L�̃R�����g�A�E�g������
//st = localStorage;
```
�̃R�����g�A�E�g���������Ă��������B  
���̏ꍇ��Web Storage�̃L���b�V���̍폜�̕��@�́uWeb Storage �폜�v�ł�����Ώo�Ă��܂��B  
�Ȃ��A�L���b�V����500���𒴂���ƃN���A����悤�ɂ��Ă��܂��B  
500����ύX����ꍇ��ip2host.inc.php��
```JavaScript
//  �L���b�V������IP�̏����
let ip_cache_size = 500;
```
��ύX���Ă��������B  

�L���b�V�����T�[�o�[���̃t�@�C���ɍ��ꍇ��500���𒴂���ƌÂ����̂���10���Â폜���܂��B  
��ɃL���b�V�����T�[�o�[���̃t�@�C���Ŏg�p����ꍇ�i�u���E�U���ɃL���b�V���������������Ȃ��A�����̃u���E�U�Ŏg�����j��ip2host.inc.php��
```JavaScript
//  ��ɃL���b�V�����T�[�o�[���̃t�@�C���Ŏg�p����ꍇ�͉��L�̃R�����g�A�E�g������
//web_storage = 0;
```
�̃R�����g�A�E�g���������Ă��������B

### Aborn
�z�X�g���̖��O���ł̂��ځ[�񏈗����s�v�ȏꍇ��ip2host.inc.php��
```JavaScript
// ���O���̂��ځ[�񏈗���K�p ����:1 ���Ȃ�:0
let aborn = 1;
```
��ύX���Ă��������B  
������Ƒ����Ȃ�Ǝv���܂��B

### Replace
�񓯊��̏������������ɂ͔O�̈׃^�C���A�E�g��ݒ肵�Ă���̂ŁA�T�[�o�[�����A�u���E�U�̃X�y�b�N�ɂ���ʂ̃��X(1-1000�Ƃ�)��\������Ƃ��ׂď����ς��Ȃ����Ƃ�����܂��B  
���̏ꍇ�̓^�C���A�E�g�̕b����ύX����Ȃ肵�Ă݂Ă��������B  

��ʃX�N���[�����ɕ\������Ă��镔���̂ݐ�������������悤�ɕύX����ꍇ�́A
```JavaScript
//  �X���\�����Ɉꊇ��������:0 ��ʃX�N���[���ŏ�������:1
let scroll_replace = 0;
```
��ύX���Ă��������B  

## ToDo
�X�}�z�p�|�b�v�A�b�v�������Ə������������B  
(�ꉞ�|�b�v�A�b�v��������ԂŃX�N���[��������Ə��������܂��B)

## License
[MIT License](https://mit-license.org/)

## Author
* junk2ool  
https://github.com/junk2ool/rep2_ip2host

## Reference
* rep2 expack �S������ by open774  
https://github.com/open774/p2-php
