# Universal Robots ROS2 Driver
유니버설 로봇은 산업뿐만 아니라 과학 연구 및 교육 분야에서 경량 협동 로봇팔 공급업체로 주도적인 위치를 차지하고 있습니다.
<center><img src="ur_robot_driver/doc/installation/initial_setup_images/e-Series.jpg" alt="Universal Robot e-Series family" style="width: 80%;"/></center>

이 드라이버는 최초의 ROS2 manipulator 드라이버 중 하나입니다. ROS2를 통해 구현된 새로운 기능으로는 지연 시간 감소, 향상된 보안, 미들웨어 설정에 대한 더 높은 유연성 등이 있습니다. 이 패키지에는 드라이버를 독립 사용 버전 혹은 MoveIt2와 함께 사용하여 빠르게 시작할 수 있는 launch 파일이 포함되어 있습니다.

이 드라이버는 [Universal_Robots_Client_Library](https://github.com/UniversalRobots/Universal_Robots_Client_Library) 기반으로 개발되었으며 긴급 정지시 일시 정지, 안전 가드 정지, 안전 설정 위반 방지를 위한 자동 속도 조절 및 티치펜던트에서 수동 속도 조절과 같은 핵심 협동 로봇 기능을 지원합니다. 또한 externalControl URCap을 통해 로봇 프로그램에 ROS2 동작을 포함시키는 것이 가능하다.

이 드라이버는 3kg 부하량에서 16kg payload까지 모든 유니버설 로봇 라인과 호환되며 CB3 및 E-시리즈 모두 포함됩니다.


이 드라이버 관련해서 [프리젠테이션 및 비디오](ur_robot_driver/doc/resources/README.md) 참고하세요.


## Build Status

<table width="100%">
  <tr>
    <th>ROS2 Distro</th>
    <th>Foxy</th>
    <th>Galactic</th>
    <th>Humble</th>
    <th>Rolling</th>
  </tr>
  <tr>
    <th>Branch</th>
    <td><a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/tree/foxy">foxy</a></td>
    <td><a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/tree/galactic">galactic</a></td>
    <td><a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/tree/humble">humble</a></td>
    <td><a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/tree/main">main</a></td>
  </tr>
  <tr>
    <th>Build Status</th>
    <td>
      <a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/foxy-binary-build.yml?query=event%3Aschedule++">
         <img src="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/foxy-binary-build.yml/badge.svg?event=schedule"
              alt="Foxy Binary Build"/>
      </a> <br />
      <a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/foxy-semi-binary-build.yml?query=event%3Aschedule++">
         <img src="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/foxy-semi-binary-build.yml/badge.svg?event=schedule"
              alt="Foxy Semi-Binary Build"/>
      </a>
    </td>
    <td>
      <a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/galactic-binary-build.yml?query=event%3Aschedule++">
         <img src="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/galactic-binary-build.yml/badge.svg?event=schedule"
              alt="Galactic Binary Build"/>
      </a> <br />
      <a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/galactic-semi-binary-build.yml?query=event%3Aschedule++">
         <img src="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/galactic-semi-binary-build.yml/badge.svg?event=schedule"
              alt="Galactic Semi-Binary Build"/>
      </a>
    </td>
    <td>
      <a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/humble-binary-build.yml?query=event%3Aschedule++">
         <img src="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/humble-binary-build.yml/badge.svg?event=schedule"
              alt="Humble Binary Build"/>
      </a> <br />
      <a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/humble-semi-binary-build.yml?query=event%3Aschedule++">
         <img src="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/humble-semi-binary-build.yml/badge.svg?event=schedule"
              alt="Humble Semi-Binary Build"/>
      </a>
    </td>
    <td>
      <a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/rolling-binary-build.yml?query=branch%3Amain+">
         <img src="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/rolling-binary-build.yml/badge.svg?branch=main"
              alt="Rolling Binary Build"/>
      </a> <br />
      <a href="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/rolling-semi-binary-build.yml?query=branch%3Amain+">
         <img src="https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver/actions/workflows/rolling-semi-binary-build.yml/badge.svg?branch=main"
              alt="Rolling Semi-Binary Build"/>
      </a>
    </td>
  </tr>
</table>


**NOTE**: 드라이버의 현재 및 미래 호환성을 검사하는 두 가지 빌드 단계가 있습니다.

1. Binary 빌드 - ROS 배포판의 릴리스된 패키지(main 및 testing)를 대상으로 합니다. 로컬에서 직접 빌드가 가능하다는 것을 보여줍니다.

   사용하는 repos 파일: `src/Universal_Robots_ROS2_Driver/Universal_Robots_ROS2_Driver-not-released.<ros-distro>.repos`

1. Semi-binary 빌드 - 릴리스된 core ROS 패키지(main 및 testing)를 대상으로 하지만, 직접적인 종속성은 소스에서 가져옵니다. 로컬에서 종속성과 함께 빌드가 가능하다는 것을 보여주며, 실패하면 다음 패키지 동기화 후 빌드가 불가능할 것으로 예상됩니다.

   사용하는 repos 파일: `src/Universal_Robots_ROS2_Driver/Universal_Robots_ROS2_Driver.repos`

각 단계는 또한 ursim을 사용하여 통합 테스트를 수행합니다. 이 테스트를 로컬에서 실행하려면 다음과 같이 활성화해야 합니다.:
  ```
  colcon build --packages-select ur_robot_driver --cmake-args -DUR_ROBOT_DRIVER_BUILD_INTEGRATION_TESTS=On
  ```


## Repository내에 Packages:

  - `ur` - 릴리즈 패키지을 위해 설치 지점을 제공하는 Meta-package
  - `ur_bringup` - 파일 launch 및 run-time 설정 예: controllers (DEPRECATED).
  - `ur_calibration` - 실제 robot에서 calibration 정보를 추출하는 도구
  - `ur_controllers` - UR 로봇 전용 컨트롤러 구현
  - `ur_dashboard_msgs` - dashboard node에서 사용하는 메시지를 정의하는 패키지
  - `ur_moveit_config` - UR 로봇용 MoveIt 구성 예제
  - `ur_robot_driver` - UR 로봇과 통신하기 위한 드라이버 / 하드웨어 인터페이스

사용중단: `ur_bringup` package는 Iron Irwini에서 제거될 예정입니다.

## 시작하기

시작하려면 기본적으로 3개 단계가 필요하다:

1. **driver 설치** (see below). You can either install this driver from binary packages or build it from source. We recommend a
binary package installation unless you want to join development and submit changes.

2. **robot 시작 & 설정하기**. Once you've installed the driver, [setup the
   robot](https://docs.ros.org/en/ros2_packages/humble/api/ur_robot_driver/installation/robot_setup.html)

Please do this step carefully and extract the calibration as explained
[here](https://docs.ros.org/en/ros2_packages/humble/api/ur_robot_driver/installation/robot_setup.html#extract-calibration-information).
Otherwise the TCP's pose will not be correct inside the ROS ecosystem.

If no real robot is required, you can [use a simulated
robot](https://docs.ros.org/en/ros2_packages/humble/api/ur_robot_driver/usage.html#usage-with-official-ur-simulator)
that will behave almost exactly like the real robot.


3. **driver 시작**. See the [usage
   documentation](https://docs.ros.org/en/ros2_packages/humble/api/ur_robot_driver/usage.html) for
   details.

### binary 패캐지에서 설치하기
1. [Install ROS2](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html). This
      branch supports only ROS2 Humble. For other ROS2 versions, please see the respective
      branches.
2. Install the driver using
   ```
   sudo apt-get install ros-${ROS_DISTRO}-ur
   ```

### Build from source
소스 코드로부터 빌드를 하기 전에 실제로 이렇게 하는 것이 필요한 것인지 확인하십시오.
소스 코드로부터 빌드하는 것은 특히 의존성 관리와 관련하여 특별한 처리가 필요할 수 있습니다. 의존성은 시간이 지남에 따라 변경될 수 있습니다. 상위 패키지(라이브러리 등)는 기능/API를 변경하여 이 저장소에서 변경 사항이 필요할 수 있습니다. 
따라서 이 저장소의 소스 빌드는 특정 버전의 상위 저장소가 있어야 빌드가 실패하지 않도록 할 수 있습니다.
아래 단계를 정확히 따라 처음부터 시작하면 항상 작동해야 하지만, 간단히 가져와서 빌드하는 것은 때때로 실패할 수 있습니다.

1. [ROS2 설치](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html).
   ROS2 humblea만 지원하는 brach 입니다.

   Once installed, please make sure to actually [source ROS2](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html#source-the-setup-files) before proceeding.

3. `colcon` 확장 및 `vcs`를 설치:
   ```
   sudo apt install python3-colcon-common-extensions python3-vcstool
   ```

4. 새로운 ROS2 workspace 생성하기:
   ```
   export COLCON_WS=~/workspace/ros_ur_driver
   mkdir -p $COLCON_WS/src
   ```

5. 관련 package 복제, 의존성 설치, 컴파일, workspace를 source 하기:
   ```
   cd $COLCON_WS
   git clone -b humble https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver.git src/Universal_Robots_ROS2_Driver
   vcs import src --skip-existing --input src/Universal_Robots_ROS2_Driver/Universal_Robots_ROS2_Driver-not-released.${ROS_DISTRO}.repos
   rosdep update
   rosdep install --ignore-src --from-paths src -y
   colcon build --cmake-args -DCMAKE_BUILD_TYPE=Release
   source install/setup.bash
   ```

6. 연속적인 pull로 빌드 오류를 발생시키는 경우, 이슈를 등록하기 전에 upstream 패키지를 업데이트했는지 확인하십시오.:
   ```
   cd $COLCON_WS
   vcs import src --skip-existing --input src/Universal_Robots_ROS2_Driver/Universal_Robots_ROS2_Driver-not-released.${ROS_DISTRO}.repos
   rosdep update
   rosdep install --ignore-src --from-paths src -y
   ```

## MoveIt! 지원

이 드라이버에는 이미 [MoveIt!](https://moveit.ros.org) 지원이 내장되어 있습니다.
MoveIt과 Universal Robots ROS2 driver 연동 보기:

[![Video: MoveIt2 Demo](https://img.youtube.com/vi/d_cVXoZZ52w/0.jpg)](https://www.youtube.com/watch?v=d_cVXoZZ52w)

  *이 영상은 Rviz2용 MoveIt2 Motion Planning 위젯을 사용하여 모델링된 충돌 장면 개체 주위의 자유공간 궤적 계획을 보여줍니다.*

상세한 내용은 [MoveIt!
section](https://docs.ros.org/en/ros2_packages/humble/api/ur_robot_driver/usage.html#using-moveit)
of the [Usage guide](https://docs.ros.org/en/ros2_packages/humble/api/ur_robot_driver/usage.html)
을 참고하세요.

## 향후 변경 사항

- 현재 궤적 제어는 position 명령만 지원합니다. 향후 velocity 제어가 추가됩니다.


## 기여자 가이드라인
Git 커밋이 발생할 때마다 코드는 clang-format 14를 사용하여 자동으로 포맷됩니다. 다음 종속성이 설치되어 있는지 확인하십시오:
  ```
  pip3 install pre-commit
  sudo apt install clang-format-14
  ```

Prepare the pre-commit formatting to run like this:
  ```
  pre-commit install
  ```
