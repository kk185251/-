---
title: "Spart Win10�Ή��ɂ�����p�b�P�[�W�쐬(Install Sheild2018��)"
tags: "Win10�Ή�"
---

# �͂��߂�

InstallShield2018�𗘗p����B��{�I�ɁA�M�҂��S�������f�C�g�i�̃v���W�F�N�g��O��Ƃ��Đi�߂邽�߁A�t�H���_�p�X�Ȃǂ͈Ⴄ�\��������B�����́A�����̒S�����Ă���v���W�F�N�g�ɒu�������Č��i�߂Ăق����B  
�܂��ACustomize Package��General Package��2��ΏۂƂ��Ă���B2�̃p�b�P�[�W�ňႤ�ݒ�̎d��������ꍇ�́A���̎|���L�ڂ���̂ň��S���Ăق����B

# �쐬���@

## Install Shield2018�𗧂��グ��܂�
�q��̃p�b�P�[�W�쐬���܂œ���B

�ȉ��̃l�b�g���[�N�p�X�ɐڑ�����B
    \\153.59.51.164
    \\153...169?

�p�X���[�h��  
User/mono, Password/password

�q��̃p�b�P�[�W�쐬���̃t�H���_�Ɉړ�����B  
Win10�p�p�b�P�[�W�쐬���p�̃t�H���_��V�K�쐬����B

Windows���j���[�́u���ׂẴv���O�����v����InstallShield�t�H���_��InstallShield2018���N������B

## Install Shield2018

Project Tasks��create new project��I������B

Common�^�u��InstallScript Project��I������B

�v���W�F�N�g�������肷��B���O�́A�ڋq�於�̕����ǂ���������Ȃ��B(���v���W�F�N�g�̑����ǂ̂悤�Ȗ��̂ɂȂ��Ă���̂��Q�l�ɂ��Č��߂�Ɠ��ꂷ��̂ŗǂ�)

Location��Browse�{�^������������B
�쐬�����Z�b�g�A�b�v(.ism)���ǂ��ɔz�u����̂����肷��B(�������A���̃p�b�P�[�W���ǂ��ɔz�u����Ă���̂��m�F���Ĕz�u�ꏊ�����߂������ǂ�)

�����́uCreate ~ �v�Ƀ`�F�b�N��t����B

���q��Ɠ��l�ɐV�K�쐬�����t�H���_�̒����ɓ����B

OK��I������B

�����ɁA���������ڂ�����ł���B

Application Information��I������B

Installtion Interview�@  
�S�Ẵ`�F�b�N�{�^�����uNo�v�ɂ���B

Build Install  
single executable�ɂ̂݃`�F�b�N������

Install Designer  
General info  
�ݒ肪�����Ă��邩�m�F����B  
TargetDir �W�J���path�ł���B
�l��ύX����
```
SPART
�ύX��FC:\opos\Application\SS

Mex SPART
�ύX��FC:\software\ncr\res
```
�uexecutable file�v�̐ݒ�l�͍폜����B

�ۑ�����B

�uproduct code�v�����邪�A����̓��j�[�NID�ł���B
�܂�A���v���W�F�N�g�Ƃ�product code�͂��Ԃ��Ă͂����Ȃ��B���Ԃ�Ȃ��悤�ɂ���B(�������A��{�I�ɐV�����v���W�F�N�g���쐬�����Ȃ��ӂ�ID�ł���Ǝv��)

�G�N�X�v���[���̓��v���W�F�N�g��Win10�p�ł͂Ȃ��p�b�P�[�W�쐬������ADATA�t�H���_���R�s�[����  

�f�B���N�g���K�w��Win10�𓝈ꂷ�邱�ƁB���̕����Ǘ����₷�����y�Ȃ̂�

�����������Ă��Ȃ��Ȃ�쐬�����v���W�F�N�g(.ism)���N������B

project assistant�^�u�́uApplication Files�v�́uApplication Target Folder�v��I������B

Win10�p�̃p�b�P�[�W�ɃR�s�[���Ă���Data�t�H���_���̊e�t�H���_��Drag&Drop����B  
���J�Ɉ��S�ɐݒ肵�������߁A1���s�����ƁB  
�X�V���Ȃ��ƁA�ǉ������̂���ʏ�ɔ��f����Ȃ����߁A�E�N���b�N����uReflesh�v���N���b�N����ƁA�X�V�����B

**���������͒��J�ɂ��Ȃ��ƃp�b�P�[�W�쐬���āA���z���ɓW�J��ASPart�̋N���Ɏ��s���邽�ߒ��ӂ���B**  

Installtion Designer�^�u��I������B  
Orgenization��setup design���Adefault feature�AdefaultComponent���܂��͍폜����B

��قǁuApprication Target Folder�v�ɒǉ������t�H���_���uFiles�v�Ƃ������̂ō쐬����Ă��邽�߁A���̖��O��ǉ������t�H���_���ƈꏏ�ɂ���B

### Data�t�H���_�̐ݒ�
�܂��A���q��̑O�p�b�P�[�W��setup.rul���J���B

�ݒ�Ώۂ̃t�H���_���Ŗ��O����(Ctrl + F)������BsvTarget������"INCLUDE_SUBDIR"������ƁAAlways�ASELFREG������ƁAself-register��Yes�Ɛݒ肷��B

�ݒ�ŋA��̂́AOverwrite��self-registory�ł���BOverwrite�́A�ǂ̂悤�ɏ㏑�����邩�ݒ肷��v���p�e�B�ł���A��{"Always"�Őݒ肷��BAlways�͓����t�ŋ����I�ɏ㏑������Ӗ������B
selfregester�͊�{server�t�H���_��program�t�H���_��dll�Aexe�̎��s�t�@�C���Őݒ肷�邱�Ƃ������B���W�X�g���o�^���邩�̐ݒ�B

setup.rul��svTarget�̊i�[��ɂ���āADestination���ς�邽�߁A�����͂悭���Đݒ肵�Ȃ��Ƃ����Ȃ��B
��
svTarget => C\\OPOS\\
TargetDisk => C:\\OPOS\\Application\\SS\\

Application Data\\File&Folders\\Application Target Folder\\
�t�H���_�����ɉ����Ȃ���΂��̃t�H���_�������B��������ꍇ�́ADesination�̐ݒ肪�Ⴄ�\��������B
�������AApplication Target Folder��C:\\OPOS\\�ł��邽�߁AOPOS�����ɔz�u�ꏊ��ݒ肵�Ă���t�H���_�͍폜���Ȃ��Ă��悢

���̍�Ƃ�Data���̂��ׂẴt�H���_�Őݒ肷��B

System Configuration��Program menu\\NCR�͍폜���Ă悢�B

ModifysetupINI.bas��package name = Media..\\Disk Images\\Disk1\\setup_out.INI��App name�������Ă��邩�Bsetup_in.txt�Ƃ������Ă��邩�B�Ⴄ�ꍇ�́A���킹��B
ProductID��InstallShield��GeneralInformation��product code�̐����񂾂��R�s�y����B

ScriptFiles�t�H���_�͑��q�悩��R�s�[����B(Setup.rul�����W�b�N�������ɈႤ����)  
setup.rul���m�F����B  
��{�I�ɑO�p�b�P�[�W��setup.rul�𐳂����O��Ƃ��Ă��邽�߁A����Ȃ��L�q�͒ǋL����B�������A�O�̃p�b�P�[�W��InstallShield��Install Shield2015�ƈႤ�o�[�W�����ł��邽�߁A�R�[�h�̋L�q�͈قȂ��Ă���B�ł��邽�߁A�K������ׂ��|�C���g�́A�p�����[�^��`(#define ~)�����ׂĂ�����Ă��邩�A���W�X�g���o�^����R�[�h�̋L�q�ɑ���Ȃ��Ƃ���͂Ȃ����ACreateDir�֐��͍����Ă���̂��m�F����B

setup.rul���E�N���b�N���A"compile"��I���B�G���[���o�Ȃ��Ȃ�OK�B

project Assistant��Build Installtion�ŁASingle�`�̂݃`�F�b�N���ABuild Installtion���N���b�N�B

Media\\Release\\Release�͍폜����B
SINGLE\_....IMAGE�����邽�߁A���ꂩ��p�b�P�[�W���r���h�������ꍇ�́ABuild�^�u��SINGLE_IMAGE�Ńr���h����B

Support Files/Billboards\\Advanced Files\\Disk1\\�ɁANewNCR.bmp�AVERSION.INI��ǉ�����B�ǉ�����t�@�C�����́ASupport files\\Disk1\\����R�s�[����B

Media\\Release\\Single_IMAGE�́uevnet�v�^�u�AExecude bat path�ɂ́Aposbuild_option.bat�܂ł̃p�X��ݒ肷��B

BUILD�^�u��SINGLE_IMGE(F7)��I������ƁA�p�b�P�[�W���쐬�ł���B

Customize pkg�́A�C�����̃p�b�P�[�W�݂̂ō쐬����Ă���B����́ASDM(Software Download Manager�A�Г��p��)�z�M�œX�܂�POS�ɓW�J����邽�߁A�ł��邾���f�[�^�T�C�Y������������ړI������B

General pkg�́AOPOS�̃x�[�X�ƂȂ�f�[�^�ł���A�쐬�������قǂ̂��Ƃ��Ȃ������{�͕ς��Ȃ��BOPOS�̊�{���W���[���̃p�b�P�[�W�ł���B

# �N���m�F

GeneralPackage�𓖂Ă�B�ċN������BPOS�A�v�����N�������A���W�X�g���o�^���s���B

CustmizePackage�𓖂Ă�B�ċN������B�G���[���o�Ȃ����OK�B�ł���Log�����Č�������肷��B
