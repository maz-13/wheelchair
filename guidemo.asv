function varargout = guidemo(varargin)
% GUIDEMO M-file for guidemo.fig

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @guidemo_OpeningFcn, ...
                   'gui_OutputFcn',  @guidemo_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT


% --- Executes just before guidemo is made visible.
function guidemo_OpeningFcn(hObject, eventdata, handles, varargin)

% Choose default command line output for guidemo
handles.output = hObject;
aaa='Wait till initialization completes';
set(handles.edit1,'String',aaa);
a=imread('left.jpg');
axes(handles.axes4);
imshow(a);


b=imread('right.jpg');
axes(handles.axes2);
imshow(b);

c=imread('forward.jpg');
axes(handles.axes1);
imshow(c);

d=imread('backward.jpg');
axes(handles.axes3);
imshow(d);


instrhwinfo('Bluetooth','HC_05');

bt = Bluetooth('HC_05', 1);

fopen(bt)


handles.bt=bt;



aaa='Initialization Completes ,Press Start';
set(handles.edit1,'String',aaa);

% Update handles structure
guidata(hObject, handles);

% UIWAIT makes guidemo wait for user response (see UIRESUME)
% uiwait(handles.figure1);


% --- Outputs from this function are returned to the command line.
function varargout = guidemo_OutputFcn(hObject, eventdata, handles) 

% Get default command line output from handles structure
varargout{1} = handles.output;



function edit1_Callback(hObject, eventdata, handles)

% --- Executes during object creation, after setting all properties.
function edit1_CreateFcn(hObject, eventdata, handles)

if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

function edit3_Callback(hObject, eventdata, handles)

% --- Executes during object creation, after setting all properties.
function edit3_CreateFcn(hObject, eventdata, handles)
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


% --- Executes on button press in Start.
function Start_Callback(hObject, eventdata, handles)
bt=handles.bt;

aaa='Acquiring EEG Signal';
set(handles.edit1,'String',aaa);
condition=0;
returncommand=0;
data = zeros(1,256);    %preallocate buffer

portnum1 = 5;   %COM Port # 
comPortName1 = sprintf('\\\\.\\COM%d', portnum1);
TG_BAUD_57600 =      57600;
TG_STREAM_PACKETS =     0;
TG_DATA_RAW =         4;
loadlibrary('thinkgear64.dll');
fprintf('thinkgear64.dll loaded\n');
% dllVersion = calllib('thinkgear64', 'TG_GetDriverVersion');
% fprintf('thinkgear64 DLL version: %d\n', dllVersion );
connectionId1 = calllib('thinkgear64', 'TG_GetNewConnectionId');
if ( connectionId1 < 0 )
    error( sprintf( 'ERROR: TG_GetNewConnectionId() returned %d.\n', connectionId1 ) );
end;





i=0;
while i< 3



currentpos=3;
c=imread('forwardc.jpg');
axes(handles.axes1);
imshow(c);
aa='Blink to Choose Forward';
bb='No Blinks Detected'
        set(handles.edit3,'String',bb);
set(handles.edit1,'String',aa);
pause(1);

readblink(bt,connectionId1,comPortName1,TG_BAUD_57600,TG_STREAM_PACKETS,TG_DATA_RAW,hObject, eventdata, handles,currentpos);

currentpos=2;
b=imread('rightc.jpg');
axes(handles.axes2);
imshow(b);
aa='Blink to Choose Right';
set(handles.edit1,'String',aa);
bb='No Blinks Detected'
        set(handles.edit3,'String',bb);
pause(1);
readblink(bt,connectionId1,comPortName1,TG_BAUD_57600,TG_STREAM_PACKETS,TG_DATA_RAW,hObject, eventdata, handles,currentpos);
currentpos=4;

d=imread('backwardc.jpg');
axes(handles.axes3);
imshow(d);
aa='Blink to Choose Backward';
set(handles.edit1,'String',aa);
bb='No Blinks Detected'
        set(handles.edit3,'String',bb);
pause(1);

readblink(bt,connectionId1,comPortName1,TG_BAUD_57600,TG_STREAM_PACKETS,TG_DATA_RAW,hObject, eventdata, handles,currentpos);
currentpos=1;
a=imread('leftc.jpg');
axes(handles.axes4);
imshow(a);
aa='Blink to Choose Left';
set(handles.edit1,'String',aa);
bb='No Blinks Detected'
        set(handles.edit3,'String',bb);
        pause(1);

readblink(bt,connectionId1,comPortName1,TG_BAUD_57600,TG_STREAM_PACKETS,TG_DATA_RAW,hObject, eventdata, handles,currentpos);

%%%relaod images
a=imread('left.jpg');
axes(handles.axes4);
imshow(a);


b=imread('right.jpg');
axes(handles.axes2);
imshow(b);

c=imread('forward.jpg');
axes(handles.axes1);
imshow(c);

d=imread('backward.jpg');
axes(handles.axes3);
imshow(d);
%%%%%%%%%%%%%%

i=i+1;
end
                 fwrite(bt,'S');
aaa='Press Start to Restart';
set(handles.edit1,'String',aaa);

function readblink(bt,connectionId1,comPortName1,TG_BAUD_57600,TG_STREAM_PACKETS,TG_DATA_RAW,hObject, eventdata, handles,currentpos)

bt=handles.bt;
connectionId1 = calllib('thinkgear64', 'TG_GetNewConnectionId');
if ( connectionId1 < 0 )
    error( sprintf( 'ERROR: TG_GetNewConnectionId() returned %d.\n', connectionId1 ) );
end;

% Attempt to connect the connection ID handle to serial port "COM3"
errCode = calllib('thinkgear64', 'TG_Connect',  connectionId1,comPortName1,TG_BAUD_57600,TG_STREAM_PACKETS );
if ( errCode < 0 )
    error( sprintf( 'ERROR: TG_Connect() returned %d.\n', errCode ) );
end

fprintf( 'Connected.  detecting blinks...\n' );


bb='Ready to capture Blinks'
        set(handles.edit3,'String',bb);

%%
%record data

j = 0;
i = 0;

%%%%%%%%%%%%choose left

while (i < 2240)   %loop for 20 seconds
    if (calllib('thinkgear64','TG_ReadPackets',connectionId1,1) == 1)   %if a packet was read...
        
      %  if (calllib('thinkgear64','TG_GetValueStatus',connectionId1,TG_DATA_RAW) ~= 0)   %if RAW has been updated 
            j = j + 1;
            i = i + 1;
            data(j) = calllib('thinkgear64','TG_GetValue',connectionId1,TG_DATA_RAW);
      %  end
    end
      if (j == 256)
     axes(handles.axes6);
          plotRAW(data);            %plot the data, update every .5 seconds (256 points)
       out=max(data);
       out1=min(data);
       if ((out > 300)  && (out1 < -300))
        amp=5 
        fs=1000  % sampling frequency
        duration=1
        freq=100
        values=0:1/fs:duration;
        a=amp*sin(2*pi* freq*values)
        sound(a)
        aa='Blink detected';
        switch currentpos
          case 1
                a=imread('lefts.jpg');
                axes(handles.axes4);
                imshow(a);
                fwrite(bt,'L');

                pause(1);

          case 2
                b=imread('rights.jpg');
                axes(handles.axes2);
                imshow(b);
                fwrite(bt,'R');

                 pause(1);

          case 3
                c=imread('forwards.jpg');
                axes(handles.axes1);
                imshow(c);
                fwrite(bt,'F');

                pause(1);
          case 4
                d=imread('backwards.jpg');
                axes(handles.axes3);
                imshow(d);
                fwrite(bt,'B');

                pause(1);

        end
        set(handles.edit3,'String',aa);
        pause(1);
        break
        
       end
        j = 0;
    end
    
end
%disconnect             
calllib('thinkgear64', 'TG_FreeConnection', connectionId1 );
