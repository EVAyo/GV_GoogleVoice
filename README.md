## Google Voice ����/�Զ����ͼ��ظ���Ϣ

### һ���Զ�������Ϣ

1��ע���¼ [IFTTT](https://www.moeelf.com/go/aHR0cHM6Ly9pZnR0dC5jb20=)
2������ [Keep Google Voice Active (Send Messege)](https://www.moeelf.com/go/aHR0cHM6Ly9pZnR0dC5jb20vYXBwbGV0cy9Tc254VFlaSi1rZWVwLWdvb2dsZS12b2ljZS1hY3RpdmUtc2VuZC1tZXNzZWdl) (ʱ��ע��ѡ��BeiJing�������Լ����巢�͵�ʱ�估������Ϣ�����ݡ�)
3�����úú󼴿��Զ������ GV �뷢����Ϣ�ˡ������������һ����������ʱ�������ʱ����ԡ��������Ѿ����Թ���û������ġ���


### �����Զ��ظ���Ϣ

1������ GV������ GV ������������ѡ�����Ϣת���������ʼ����򿪡�
2������ Gmail����������ѡ�񡰹����������εĵ�ַ�� --> �������µĹ������� --> �ڷ����˴���д ��@txt.voice.google.com��������ͼ��ʾ��

![1](https://www.moeelf.com/action/Watermark?mark=L3Vzci91cGxvYWRzLzIwMTkvMDUvODM4MzU0ODMyLnBuZw==)

3����������������������ڵ����ĶԻ�������ѡ���ǩ�� --> ���½���ǩ���������ǩ��Ϊ��autoreply��������������ɡ�

![2](https://www.moeelf.com/action/Watermark?mark=L3Vzci91cGxvYWRzLzIwMTkvMDUvMTA4MTg5MDI4OS5wbmc=)
4��ѡ������ͼ��ʾ���������������������ɡ�

![3](https://www.moeelf.com/action/Watermark?mark=L3Vzci91cGxvYWRzLzIwMTkvMDUvMzYwODM1MDMzMy5wbmc=)
5����¼ Google Drive���������Ͻǵġ��½���������ͼ�½�һ�� Google App Script��(��δ�ҵ������ڡ���������Ӧ�á�������ҡ�Google Apps Script������һ�¾����ˡ�)

![4](https://www.moeelf.com/action/Watermark?mark=L3Vzci91cGxvYWRzLzIwMTkvMDUvNDEwOTkyNDk4OS5wbmc=)

6����������Ĵ����滻���еĴ��롣
```bash
function autoReplier() {
  var labelObj = GmailApp.getUserLabelByName('autoreply');
  var gmailThreads;
  var messages;
  var messagecount;
  var sender;
  var num = 9;  //���������Զ��ظ��ʼ��Ĵ�����Ϊ��ֹ���˶����Զ��ظ��������ʹ����ﵽ 9 ʱ�����Զ��ظ�����
  var hours = 12;  //����Զ��ظ������������������õ�ֵ�����˶���Сʱ���ֿ����Զ��ظ���
    
  for (var gg = 0; gg < labelObj.getUnreadCount(); gg++) {
    gmailThreads = labelObj.getThreads()[gg];
    messages = gmailThreads.getMessages();
    messagecount = gmailThreads.getMessageCount();
    for (var ii = 0; ii < messages.length; ii++) {
      
      if (messages[ii].isUnread()) {
        
        msg = messages[ii].getPlainBody();
        sender = messages[ii].getFrom(); 
 
        if (messagecount < num){
          MailApp.sendEmail(sender, "Auto Reply", "Hi, ���ã�����һ���Զ��ظ����ţ��������� Google Apps Script �Զ�������");
        }else if( (messages[messagecount - 1].getDate().getTime() - messages[messagecount - num].getDate().getTime()) > hours * 60 * 60 * 1000 ){
          MailApp.sendEmail(sender, "Auto Reply", "Hi, ���ã�����һ���Զ��ظ����ţ��������� Google Apps Script �Զ�������");
        }
        messages[ii].markRead();
        messages[ii].moveToTrash();
 
      }
    }
  }
}
```

7��������棬�ڵ����ĶԻ����������Ҫ��ʾ�����ƣ����磺autoReplier���ٵ��������ԡ�����ʾ����Ȩ���㰴��ʾ��Ȩ���ɡ���Ȩ������ʾû���ҵ��ļ�֮��ģ����ùܡ�
8���ٴε�������ԡ������û���κ���ʾ˵���ű�û�д�����Ҳ�����ڡ��鿴�� --> ����־�� --> ��Apps �ű���Ϣ���ġ��в鿴�ű�����״̬�������ʾ״̬Ϊ��������ʾ�ű�û�д���

![5](https://www.moeelf.com/action/Watermark?mark=L3Vzci91cGxvYWRzLzIwMTkvMDUvNzA2MzQ2ODQ1LnBuZw==)

9���������޸ġ� --> ����ǰ��Ŀ�Ĵ������� --> ���½ǵġ���Ӵ�������������ͼ���úñ��漴�ɡ�

![6](https://www.moeelf.com/action/Watermark?mark=L3Vzci91cGxvYWRzLzIwMTkvMDUvNDE2MDYyNjQ5Mi5wbmc=)

10�����ˣ���������Ը��Լ���һ�����������ˡ�  �������������ԣ�

����ת��[�Ⱦ���](https://www.moeelf.com)ԭ�ĵ�ַ��https://www.moeelf.com/archives/4.html
