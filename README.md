# import java.time.DayOfWeek;
import java.util.Scanner;
        //Учитывая день недели, закодированный как 1 = Пн, 2 = Вторник, ... 6 = Сб,7-Вс
        //и логическое значение, указывающее, что мы находимся в отпуске, возвращает строку вида "10:00",
        //указывающую, когда Будильник должен зазвонить. В будние дни будильник должен быть «7:00»,
        //а в выходные - «10:00». Если мы  в отпуске - тогда в будние дни это должно быть "10:00",
        //а в выходные дни оно должно быть "выключено".
public class JustPrograming {
            public static void main(String[] args) {
                Scanner in = new Scanner(System.in);
                int DayCount;
                String Status="Нет информации";

                do {
                    System.out.print("Введите день недели по счету:");
                    DayCount = in.nextInt();
                } while (DayCount < 1 || DayCount > 7);

                System.out.print("Вы сейчас в отпуске(Да или Нет):");
                Status=in.next();

                boolean vacation=StatusVacation(Status);

                String DayName = DayOfWeek(DayCount);
                String AlarmTime=AlarmClock(DayCount,vacation);

                System.out.println("Будильник заиграет сегодня в "+AlarmTime);
                System.out.print("День недели:"+DayName);
            }


static String AlarmClock(int DayCount,boolean vacation){

                    if(vacation&DayCount<6) return "10:00";

                    else if(vacation&DayCount>5)    return "Off";

                    else if(!vacation&DayCount<6) return "7:00";

                    else if(!vacation & DayCount>5)return "10:00";

                    else return "Произошла внутренняя ошибка при расчете";
            }


           static   String DayOfWeek(int Day)
            {
                String Day_Week="";
                switch (Day) {
                    case 1:
                         Day_Week = "Понедельник";
                   break;
                    case 2:
                         Day_Week = "Вторник";
                        break;
                    case 3:
                         Day_Week = "Среда";
                        break;
                    case 4:
                         Day_Week = "Четверг";
                        break;
                    case 5:
                         Day_Week = "Пятница";
                        break;
                    case 6:
                         Day_Week = "Суббота";
                        break;
                    case 7:
                         Day_Week = "Воскресенье";
                        break;
                }
                return Day_Week;
            }

            static boolean StatusVacation(String Status){

                if(Status.equals("Нет")||Status.equals("нет")||Status.equals("Не"))    return false;

                else if(Status.equals("Да")||Status.equals("да"))  return true;
                else{
               System.out.print("Произошла  ошибка!Скорее всего вы ввели неккоректную инфрмацию");
                System.exit(0);
                 return false;
            }
            }
        }

